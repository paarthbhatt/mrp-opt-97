# Implementation Guide: The "Lethal Engineer" Path

This guide outlines how to integrate MRP-OPT-97 into your existing agentic workflows.

## Step 1: Intent Pre-Processing
Before sending a task to an LLM, use a "Router" class (e.g., Gemini-Flash) to categorize the intent. 
```python
def route_task(user_input):
    # Quick, cheap classification
    intent = router.classify(user_input)
    return intent
```

## Step 2: Artifact Conversion
If your task involves a file > 5KB, do not send the text. 
1. Upload to your internal artifact store.
2. Send the URI and SHA256 hash.
3. Your recipient agent should use `Range` requests to pull only what it needs.

## Step 3: Confidence Gating
Never let a cheap model handle a high-uncertainty task.
```python
if router.confidence < 0.85:
    return escalate_to_tier("Reasoning")
```

## Step 4: Outcome Verification
Audit your savings. If your `Token_Spend / Task_Complexity` ratio doesn't drop by 90%+, you have a context leak.
