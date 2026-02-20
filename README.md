# Intel
Multi agent research team
import time
from typing import List, Dict
import random

# Simulate compressed context sharing by summarizing messages
def compress_context(messages: List[str]) -> str:
    # Simple compression: join last 3 messages and truncate
    combined = " ".join(messages[-3:])
    return combined[:200]  # limit context size

class Agent:
    def __init__(self, name: str, specialty: str):
        self.name = name
        self.specialty = specialty
        self.memory = []
    
    def receive_message(self, message: str):
        self.memory.append(message)

    def respond(self, context: str) -> str:
        # Simulate research-oriented response based on context and specialty
        response = f"[{self.name} - {self.specialty}] Analysis based on context: '{context[:50]}...'"
        # Add random research insight for simplicity
        insights = [
            "Suggest optimizing token usage.",
            "Propose to shard dataset for parallel processing.",
            "Recommend using reinforcement learning for agent coordination.",
            "Identify potential bottlenecks in communication.",
            "Highlight recent advances in multi-agent systems."
        ]
        return response + " " + random.choice(insights)

class MultiAgentChatbot:
    def __init__(self):
        self.agents = [
            Agent("Alice", "Data Processing"),
            Agent("Bob", "Coordination"),
            Agent("Clara", "Optimization")
        ]
        self.global_memory = []
        self.user_progress = {}

    def user_select_project(self, user_id: str):
        self.user_progress[user_id] = {"project