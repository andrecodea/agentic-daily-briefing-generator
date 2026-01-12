# 🌐 Automated Daily Briefing

This project uses **n8n** to automate the generation, compilation, and delivery of daily briefings, which include information collected from sources like Google Calendar, Gmail, Google Tasks, and OpenWeatherMap. In summary, the workflow acts as a personalized morning assistant, delivering all relevant information directly on Telegram.

---

## 🔧 Workflow Architecture

Below is a visual representation of the architecture, highlighting its main components:

```mermaid
flowchart TD
    A[⏰ Scheduled Trigger] -->|6:00 AM| B[🔍 Data Collection]
    B --> B1[🌧️ OpenWeatherMap (Weather)]
    B --> B2[📅 Google Calendar (Daily Events)]
    B --> B3[📧 Gmail (Recent Emails)]
    B --> B4[📝 Google Tasks (Tasks)]
    B1 --> C[🔄 Merge Data]
    B2 --> C[🔄 Merge Data]
    B3 --> C[🔄 Merge Data]
    B4 --> C[🔄 Merge Data]
    C --> D[🧠 Refinement: AI for Summarization and Briefing Generation]
    D --> E{✔️ Content Verification}
    E -->|Content Verified| F[📤 Send Briefing via Telegram]
    E -->|Error or No Data| G[❌ Error Message]
```

---

## 🖇️ Detailed Explanation

### 🔹 Scheduled Trigger
The workflow is automatically initiated every day at 6:00 AM, ensuring timely execution.

### 🔹 Data Collection
1. **Weather:** Retrieved via OpenWeatherMap API, providing current conditions and base forecasts.
2. **Events:** Pulled from the connected Google Calendar.
3. **Emails:** Captures a summary of the 5 most recent emails in the user's Gmail inbox.
4. **Tasks:** Fetches pending tasks from Google Tasks.

### 🔹 Data Merging and Summarization
Collected data is consolidated into a single structure. JavaScript scripts ensure that each data type is formatted clearly for the AI agent.

### 🔹 Briefing Generation
An AI model is used to analyze the data and generate a briefing with a specific format, meeting constraints such as compatibility with basic HTML and avoiding unsupported tags in Telegram.

### 🔹 Verification and Delivery
If the generated briefing is valid, it is sent to the user via the Telegram API. If not, an error message is sent alerting the user to a failure in generation.

---

## 🚀 How to Use

1. **Configuration:**
   - Set credentials for Google, OpenWeatherMap, and Telegram.
2. **Scheduling:**
   - Adjust the trigger node's scheduled time, if necessary.
3. **Execution:**
   - Test the workflow to ensure it is working as expected.

---

## 🛠️ Dependencies

- **n8n**: Automation tool.
- **APIs Used**: Google Calendar, Gmail, Google Tasks, OpenWeatherMap, Telegram.
- **AI Models**: GPT-series via OpenRouter API or OpenAI.

---

## 🤝 Contributions
Contributions are welcome! Feel free to open issues or submit PRs to the repository.
