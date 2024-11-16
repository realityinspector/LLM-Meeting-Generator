# Meeting Simulation Tool - README

## Overview
This script automates a meeting simulation process using OpenAI's API for tasks like validating a meeting agenda, creating agent profiles, simulating conversations, and generating summaries. It uses asyncio for asynchronous processing and includes robust error handling and retry mechanisms with tenacity.

---

## Features
- **Asynchronous API Calls:** Efficient use of OpenAI API for chat completions.
- **Rate Limiting:** Adheres to API usage limits using a time-based queue.
- **Task Queue Management:** Sequential execution of meeting-related tasks with status tracking.
- **JSON Output:** Outputs results (parsed agenda, agent profiles, simulated conversations, and summary) in a structured JSON file.
- **Error Handling:** Graceful handling of errors, retries for recoverable errors, and detailed logging.

---

## Prerequisites
- **Python 3.8+**
- Required packages (install via pip):
  ```bash
  pip install aiohttp tenacity openai
  ```

- Set the `OPENAI_API_KEY` environment variable with your OpenAI API key.

---

## File Structure
- `config/system_prompts.json`: Configuration file for system prompts.
- `meeting_agenda.txt`: Input file containing the meeting agenda.
- `meeting_transcript.json`: Output file containing the results.
- `task_queue.json`: File used to track the progress and status of tasks.

---

## Installation
1. Clone this repository.
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Set the `OPENAI_API_KEY` environment variable:
   ```bash
   export OPENAI_API_KEY=your_api_key_here
   ```

---

## Usage
Run the script:
```bash
python script_name.py
```

The script will:
1. Load the meeting agenda from `meeting_agenda.txt`.
2. Validate and parse the agenda using OpenAI API.
3. Create agent profiles for meeting participants.
4. Simulate conversations based on the agenda.
5. Generate a summary of the meeting.
6. Write the output to `meeting_transcript.json`.

---

## Task Workflow
The tasks are processed sequentially:
1. **Load Config:** Read system prompts from `system_prompts.json`.
2. **Load Agenda:** Read the meeting agenda from `meeting_agenda.txt`.
3. **Validate Agenda:** Validate agenda content using OpenAI.
4. **Parse Agenda:** Parse agenda items into structured JSON.
5. **Create Agent Profiles:** Generate detailed profiles for attendees.
6. **Simulate Conversation:** Simulate discussions based on agenda items and agent profiles.
7. **Generate Summary:** Create a meeting summary.
8. **Write Output:** Save the results to `meeting_transcript.json`.

---

## Configuration
The system prompts and API parameters (temperature, max tokens, etc.) can be configured in the `config/system_prompts.json` file.

---

## Logging
Logs are written to the console with timestamps and details about each step and any errors encountered.

---

## Error Handling
- Retries for transient errors using tenacity.
- Logs detailed error information for debugging.
- Invalid task structures or agenda inputs halt execution with a logged error.

---

## Output
- The final JSON output contains:
  - **Agenda:** Parsed meeting agenda.
  - **Attendees:** Profiles of meeting participants.
  - **Conversation:** Simulated meeting dialogue.
  - **Summary:** High-level summary of the meeting.

---

## Development Notes
- Modify `CONFIG_FILE`, `INPUT_FILE`, and `OUTPUT_FILE` constants as needed.
- Ensure proper formatting in `meeting_agenda.txt` for smooth parsing.

---

## License
This project is licensed under the MIT License.

---

## Contact
For questions or issues, contact the script maintainer.