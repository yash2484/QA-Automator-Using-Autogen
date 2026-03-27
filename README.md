# 🚀 Autonomous DDT Framework  
### Multi-Agent Data-Driven Testing using AutoGen

An **AI-powered, multi-agent testing framework** that automates the complete QA lifecycle — from **synthetic test data generation → test script creation → execution → self-healing**.

Built using **Microsoft AutoGen**, this system simulates a real-world QA team with specialized agents collaborating autonomously.

## 📌 Overview

Traditional QA pipelines are:
- Manual  
- Time-consuming  
- Hard to scale  

This project solves that by introducing a **self-operating QA system powered by LLM agents**.

### 💡 What it does:
- Generates realistic test datasets  
- Writes pytest automation scripts  
- Executes tests automatically  
- Fixes failures via a self-healing loop  

## 🧠 Architecture

UserProxy (Test Runner)
        ↓
Data Architect → Generates CSV test data
        ↓
SDET Expert → Writes pytest script
        ↓
Test Runner → Executes tests
        ↓
(Self-Healing Loop if errors)

## 🤖 Agents

### 🏗️ Data Architect
- Generates synthetic test data (CSV)  
- Follows schema + validation rules  
- Covers edge cases automatically  

### 🧪 SDET Expert
- Writes pytest automation scripts  
- Uses parameterized testing  
- Simulates API behavior  

### ⚙️ Test Runner (UserProxy)
- Executes generated code  
- Captures errors  
- Routes failures back for fixes  

## 🔁 Self-Healing Loop

The core innovation of this framework:

1. Test execution fails  
2. Error traceback captured  
3. Sent back to SDET agent  
4. Script rewritten automatically  
5. Re-run until success  

✅ Fully autonomous debugging loop  

## 📂 Project Structure

ddt_framework/
│
├── main.py
├── .env
├── workspace/
│   ├── registration_test_data.csv
│   └── test_registration_api.py
└── README.md


## 🧪 Example Test Logic

Validation rules implemented:
- Age ≥ 18  
- Email contains @ and .com  
- Password ≥ 8 characters  

## 🧠 Key Concepts Used

- Multi-Agent Systems (AutoGen)  
- GroupChat Orchestration  
- Custom Speaker Selection  
- Code Execution Agents  
- Self-Healing Pipelines  

## 🚨 Common Issues

| Issue | Cause | Fix |
|------|------|-----|
| Infinite loop | No termination signal | Ensure TESTS_PASSED |
| CSV incorrect | Weak seed prompt | Define schema clearly |
| Pandas error | Missing dependency | Install or switch to csv |
| Loop not healing | Traceback missing | Ensure logs are captured |

## 💡 Why This Project Matters

This project demonstrates:
- Agentic AI systems  
- Autonomous workflows  
- Production-grade orchestration  
- AI-driven software testing  

## 🎯 Use Cases

- Automated QA pipelines  
- API testing frameworks  
- CI/CD intelligent testing  
- AI-driven DevOps tools  

## 🧩 Future Improvements

- Docker sandbox execution  
- Real API integration  
- CI/CD integration (GitHub Actions)  
- DeepEval integration for test quality scoring  
- UI dashboard for monitoring  
