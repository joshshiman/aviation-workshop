# Lab 3: Building AI Agents with watsonx Orchestrate

**Duration:** 60 minutes  
**Objective:** Create intelligent agents that analyze weather conditions and assess flight risks

---

## Overview

In this lab, you'll:
1. Build a Weather Analysis Tool using watsonx Orchestrate
2. Build a Flight Risk Assessment Tool
3. Test your tools locally
4. Deploy tools to watsonx Orchestrate

---

## Prerequisites

- ✅ Completed Lab 1 (environment setup)
- ✅ Completed Lab 2 (Kafka consumer)
- ✅ Virtual environment activated
- ✅ watsonx Orchestrate credentials configured

---

## Part 1: Understanding Orchestrate Tools (5 min)

### What Are Orchestrate Tools?

Orchestrate tools are Python functions that:
- Use the `@tool()` decorator to expose them to agents
- Have clear input/output schemas (using Pydantic)
- Can be called by AI agents to perform specific tasks
- Run in isolated containers for security

### Tool Structure

```python
from ibm_watsonx_orchestrate.agent_builder.tools import tool
from pydantic import BaseModel, Field

class ToolInput(BaseModel):
    """Define what the tool needs"""
    parameter: str = Field(description="What this parameter does")

class ToolOutput(BaseModel):
    """Define what the tool returns"""
    result: str = Field(description="What this result means")

@tool()
def my_tool(input: ToolInput) -> ToolOutput:
    """
    Clear description of what this tool does.
    The agent uses this to decide when to call the tool.
    """
    # Your logic here
    return ToolOutput(result="something")
```

---

## Part 2: Build Weather Analysis Tool (20 min)

### Step 1: Review the Template

Look at the prebuilt template in `workshop/agents/tool_template.py` to understand the structure.

### Step 2: Create Weather Analysis Tool with Bob

Copy and paste this prompt into IBM Bob:

```bash
Create a file called weather_tool.py in the workshop/agents directory with the following:

1. Import: tool decorator from ibm_watsonx_orchestrate.agent_builder.tools, BaseModel and Field from pydantic

2. Create WeatherInput class (BaseModel) with fields:
   - condition: str (Weather condition type)
   - severity: str (Severity level: Low, Medium, High)
   - visibility_km: float (Visibility in kilometers)
   - wind_speed_kmh: float (Wind speed in km/h)

3. Create WeatherAnalysis class (BaseModel) with fields:
   - risk_level: str (Overall risk: low, medium, high, critical)
   - impact_description: str (Description of aviation impact)
   - recommendations: list[str] (List of safety recommendations)

4. Create analyze_weather_severity function with @tool() decorator:
   - Takes WeatherInput as input
   - Returns WeatherAnalysis
   - Docstring: "Analyzes weather conditions and provides detailed aviation safety assessment. Use this tool when you need to understand the severity and implications of weather conditions."
   
5. Logic for risk_level:
   - If severity is "High" and visibility < 1km: risk_level = "critical"
   - If severity is "High": risk_level = "high"
   - If severity is "Medium": risk_level = "medium"
   - Otherwise: risk_level = "low"

6. Logic for recommendations based on risk_level:
   - critical/high: ["Consider flight delays or cancellations", "Monitor conditions closely", "Prepare alternate routes"]
   - medium: ["Exercise caution", "Monitor weather updates", "Brief crew on conditions"]
   - low: ["Normal operations can continue"]

7. Logic for impact_description:
   - Mention condition type
   - If visibility < 3km, mention "severely reduced visibility"
   - If wind_speed > 40kmh, mention "strong winds"
   - Format: "{condition} with {impacts}"

8. Add if __name__ == "__main__": block to test the tool with sample data:
   - Test with: Thunderstorm, High severity, 2.0km visibility, 55kmh wind
   - Handle the ToolResponse wrapper returned by @tool() decorator
   - Check for common response attributes (data, content, result, output, value)
   - Print the risk_level, impact_description, and recommendations
```

### Step 3: Test Your Weather Tool

Run the tool locally to verify it works:

```bash
cd workshop/agents
python weather_tool.py
```

**Expected Output:**
```
============================================================
WEATHER ANALYSIS TEST
============================================================
Result type: ToolResponse
Risk Level: critical
Impact Description: Thunderstorm with severely reduced visibility and strong winds
Recommendations:
  - Consider flight delays or cancellations
  - Monitor conditions closely
  - Prepare alternate routes
============================================================
```

> 💡 **Note:** The `@tool()` decorator wraps the return value in a `ToolResponse` object. The test code handles this by checking for common response attributes to extract the actual `WeatherAnalysis` data.

---

## Part 3: Build Flight Risk Assessment Tool (20 min)

### Step 1: Create Flight Risk Tool with Bob

Copy and paste this prompt into IBM Bob:

```bash
Create a file called flight_tool.py in the workshop/agents directory with the following:

1. Import: tool decorator from ibm_watsonx_orchestrate.agent_builder.tools, BaseModel and Field from pydantic

2. Create FlightRiskInput class (BaseModel) with fields:
   - flight_id: str (Flight identifier)
   - distance_to_hazard_km: float (Distance to weather hazard in km)
   - weather_severity: str (Weather severity: Low, Medium, High)
   - altitude_ft: int (Current altitude in feet)
   - speed_kmh: int (Current speed in km/h)

3. Create FlightRiskAssessment class (BaseModel) with fields:
   - risk_score: float (Risk score from 0-10)
   - recommended_action: str (Action: continue, monitor, divert, delay)
   - reasoning: str (Explanation of the assessment)

4. Create assess_flight_risk function with @tool() decorator:
   - Takes FlightRiskInput as input
   - Returns FlightRiskAssessment
   - Docstring: "Assesses risk level for a flight near a weather hazard and recommends actions. Use this tool to evaluate proximity of flights to weather hazards and provide actionable recommendations."

5. Logic for risk_score calculation (start at 0.0):
   - If distance < 20km: add 5.0
   - Else if distance < 50km: add 3.0
   - Else if distance < 100km: add 1.0
   - If weather_severity is "High": add 4.0
   - If weather_severity is "Medium": add 2.0
   - If weather_severity is "Low": add 0.5
   - If altitude < 10000ft: add 1.0
   - Cap risk_score at 10.0 using min()

6. Logic for recommended_action based on risk_score:
   - If risk_score >= 8: action = "divert"
   - Else if risk_score >= 5: action = "monitor"
   - Else if risk_score >= 3: action = "monitor"
   - Else: action = "continue"

7. Logic for reasoning based on action:
   - divert: "Critical risk: {flight_id} is {distance}km from {severity} severity weather. Immediate diversion recommended."
   - monitor (high risk): "Elevated risk: {flight_id} should be closely monitored. Consider alternate routes."
   - monitor (moderate): "Moderate risk: Continue with caution. Monitor weather updates for {flight_id}."
   - continue: "Low risk: {flight_id} can continue normal operations."

8. Add if __name__ == "__main__": block to test with:
   - flight_id: "AC123"
   - distance_to_hazard_km: 25.0
   - weather_severity: "High"
   - altitude_ft: 35000
   - speed_kmh: 850
   - Handle the ToolResponse wrapper (same as weather tool)
   - Print risk_score, recommended_action, and reasoning
```

### Step 2: Test Your Flight Risk Tool

Run the tool locally:

```bash
cd workshop/agents
python flight_tool.py
```

**Expected Output:**
```
============================================================
FLIGHT RISK ASSESSMENT TEST
============================================================
Result type: ToolResponse
Risk Score: 9.0/10
Recommended Action: divert
Reasoning: Critical risk: AC123 is 25.0km from High severity weather. Immediate diversion recommended.
============================================================
```

> 💡 **Note:** Like the weather tool, the flight tool also wraps results in a `ToolResponse` object that needs to be handled in the test code.

---

## Part 4: Deploy Tools to watsonx Orchestrate (15 min)

### Step 1: Configure Orchestrate Environment

First, add your watsonx Orchestrate environment to the CLI:

```bash
orchestrate env add -n aviation-workshop -u <your-service-instance-url>
```

Replace `<your-service-instance-url>` with your `ORCHESTRATE_API_URL` from Lab 1.

You'll be prompted to enter your API key (from Lab 1, your `ORCHESTRATE_API_KEY`).

**Expected Output:**
```
Environment 'aviation-workshop' added successfully
```

### Step 2: Activate the Environment

Activate your environment so all commands target it:

```bash
orchestrate env activate aviation-workshop
```

**Expected Output:**
```
Environment 'aviation-workshop' is now active
```

> 💡 **Note:** Authentication expires every 2 hours. If you get authentication errors later, just run `orchestrate env activate aviation-workshop` again.

### Step 3: Verify Environment

Check that your environment is active:

```bash
orchestrate env list
```

You should see `aviation-workshop` marked as active (with an asterisk or highlighted).

### Step 4: Import Weather Tool

```bash
cd workshop/agents
orchestrate tools import -k python -f weather_tool.py
```

**Expected Output:**
```
✅ Tool 'analyze_weather_severity' imported successfully
```

### Step 5: Import Flight Risk Tool

```bash
orchestrate tools import -k python -f flight_tool.py
```

**Expected Output:**
```
✅ Tool 'assess_flight_risk' imported successfully
```

### Step 6: Verify Tools Are Imported

List all your tools:

```bash
orchestrate tools list
```

You should see both tools in the list:
- `analyze_weather_severity`
- `assess_flight_risk`

---

## Part 5: Create a Supervisor Agent (Optional, 10 min)

### What Is an Agent?

An agent is a configuration that:
- Has access to specific tools
- Uses an LLM to decide which tools to call
- Can reason about complex problems
- Provides intelligent responses

### Create Agent Configuration with Bob

Copy and paste this prompt into IBM Bob:

```bash
Create a file called supervisor_agent.yaml in the workshop/agents directory with the following YAML structure:

spec_version: v1
kind: native
name: aviation_supervisor
display_name: Aviation Safety Supervisor
description: |
  Analyzes aviation safety by evaluating weather conditions and flight risks
llm: groq/openai/gpt-oss-120b
style: react
tools:
  - analyze_weather_severity
  - assess_flight_risk
instructions: |
  You are an aviation safety supervisor. Your role is to:
  1. Analyze weather conditions using the weather analysis tool
  2. Assess flight risks using the flight risk assessment tool
  3. Provide clear, actionable safety recommendations
  4. Prioritize passenger safety above all else
  
  When given weather and flight information:
  - First analyze the weather severity
  - Then assess the flight risk based on proximity
  - Provide a comprehensive safety assessment
  - Be clear and direct in your recommendations
```

### Import the Agent

```bash
cd workshop/agents
orchestrate agents import -f supervisor_agent.yaml
```

**Expected Output:**
```
✅ Agent 'aviation_supervisor' imported successfully
```

---

## Testing Your Tools (Bonus)

### Test in Orchestrate UI

1. Go to your watsonx Orchestrate instance
2. Navigate to the Agents section
3. Find your `aviation_supervisor` agent
4. Click "Test" or "Chat"
5. Try a query like:

```
Analyze this situation:
- Weather: Thunderstorm with High severity, 2km visibility, 55km/h winds
- Flight AC123 is 25km away at 35000ft altitude

What should we do?
```

The agent should:
1. Call `analyze_weather_severity` tool
2. Call `assess_flight_risk` tool
3. Provide a comprehensive recommendation

---

## Troubleshooting

### Issue: "Module not found" when testing locally

**Solution:**
```bash
# Make sure you're in the agents directory
cd workshop/agents

# Make sure venv is activated
source ../venv/bin/activate  # or ..\venv\Scripts\activate on Windows

# Run the tool
python weather_tool.py
```

### Issue: Tool import fails

**Checklist:**
- [ ] Is your Orchestrate API key correct in `.env`?
- [ ] Are you in the correct directory?
- [ ] Does the Python file have syntax errors?

**Solution:**
```bash
# Test your Orchestrate connection
orchestrate --version

# Check for Python syntax errors
python -m py_compile weather_tool.py
```

### Issue: Agent can't find tools

**Solution:**
```bash
# List all tools to verify they're imported
orchestrate tools list

# If missing, re-import
orchestrate tools import -k python -f weather_tool.py
orchestrate tools import -k python -f flight_tool.py
```

---

## Verification Checklist

Before moving to Lab 4, ensure you:

- [ ] Created `weather_tool.py` with weather analysis logic
- [ ] Created `flight_tool.py` with risk assessment logic
- [ ] Tested both tools locally and they work
- [ ] Imported both tools to watsonx Orchestrate
- [ ] Verified tools appear in `orchestrate tools list`
- [ ] (Optional) Created and imported supervisor agent
- [ ] (Optional) Tested agent in Orchestrate UI

---

## What You Learned

✅ **Orchestrate Tool Development**
- Creating tools with `@tool()` decorator
- Defining input/output schemas with Pydantic
- Writing clear docstrings for agent understanding

✅ **Business Logic Implementation**
- Risk assessment algorithms
- Conditional logic for recommendations
- Structured output formatting

✅ **Orchestrate CLI**
- Importing tools to Orchestrate
- Managing tools and agents
- Testing and verification

---

## Next Steps

🎉 **Excellent work!** You've built intelligent AI agents!

In **Lab 4**, you'll create a dashboard to:
- Visualize flights and weather on a map
- Display real-time alerts
- Show agent recommendations
- Provide an interactive interface

---

## Quick Reference

**Test Tools Locally:**
```bash
cd workshop/agents
python weather_tool.py
python flight_tool.py
```

**Import Tools:**
```bash
orchestrate tools import -k python -f weather_tool.py
orchestrate tools import -k python -f flight_tool.py
```

**List Tools:**
```bash
orchestrate tools list
```

**Import Agent:**
```bash
orchestrate agents import -f supervisor_agent.yaml
```

---

**Lab 3 Complete!** 🤖✨