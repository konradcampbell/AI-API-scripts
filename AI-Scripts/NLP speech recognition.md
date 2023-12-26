Problem statement?

How did the agent perform?

What was the goal of the call?

What actions were performed by the agent?

	-escalation?
	-did they solve it?

Install Windows C++ from https://visualstudio.microsoft.com/visual-cpp-build-tools/ 

After it is installed, click 1 boxes on the window that pops up after it is downloaded.

![[Visual Studio.png]]

Create a new python file called extraction
Install a new library 
	pip install deepgram-sdk
	If you run into any issues highlight the full link with the error, open the browser, paste it in and download the build. The execute the download.

It appears that you've provided a Python script that uses OpenAI's GPT-4 model to analyze transcripts of customer service calls. Let's break down the key components and understand the purpose of the code:
### Code Overview:

1. **Installation:**
   ```python
   from openai import OpenAI
   client = OpenAI(api_key="API Key")
   ```

   This part initializes the OpenAI client with the provided API key.

2. **Analysis Function:**
   ```python
   def analyze_transcript(call_transcript):
       # ... (uses OpenAI GPT-4 model to analyze the transcript)
   ```

   The function takes a customer service call transcript and uses the GPT-4 model to generate an after-action report in JSON format.

3. **Loop Through Audio Samples:**
   ```python
   for i, file in enumerate(os.listdir("audio_samples")):
       transcript = extract_transcript(f'audio_samples/{file}')
       analysis = analyze_transcript(transcript)
       print(f"[{i+1}/{len(os.listdir('audio_samples'))}] - {file} - {analysis}")
   ```

   This loop goes through each audio file in the "audio_samples" directory, extracts the transcript, performs analysis using GPT-4, and prints the result.

### Customer Service Call Transcripts Analysis:

Here are summaries of the analysis for each transcript:

1. **en_US_car_rental_01.wav:**
   - **Customer Sentiment:** Angry
   - **Agent Sentiment:** Neutral
   - **Problem Statement:** Issues finding rental car availability.
   - **Resolution Actions:** Agent attempted to find a rental car through back inventory, checked multiple locations and dates, confirmed no availability, calculated travel time, inquired with Hertz directly.
   - **Required Escalation:** True
   - **Resolved:** False

2. **en_US_car_rental_02.wav:**
   - **Customer Sentiment:** Neutral
   - **Agent Sentiment:** Neutral
   - **Problem Statement:** Customer needs to rent a car at the airport.
   - **Resolution Actions:** Verified customer's account, checked vehicle availability, provided pricing, offered alternative options, discussed fees, assisted with online booking, provided location code.
   - **Required Escalation:** False
   - **Resolved:** True

3. **en_US_car_rental_03.wav:**
   - **Customer Sentiment:** Upset
   - **Agent Sentiment:** Neutral
   - **Problem Statement:** Customer's car reservation lost, seeks refund.
   - **Resolution Actions:** Recorded issue details, requested receipt, submitted a refund request, advised on the need for receipt, investigated call disconnection issues.
   - **Required Escalation:** True
   - **Resolved:** False

4. **en_US_phone_service_01.wav:**
   - **Customer Sentiment:** Upset
   - **Agent Sentiment:** Neutral
   - **Problem Statement:** Poor graphics quality on devices, wants to cancel family plan.
   - **Resolution Actions:** Attempted to retain the customer, offered an exchange, processed cancellation, informed about number retention.
   - **Required Escalation:** False
   - **Resolved:** True

5. **en_US_phone_service_02.mp3:**
   - **Customer Sentiment:** Neutral
   - **Agent Sentiment:** Positive
   - **Problem Statement:** Customer received an offer for a Blackberry torch exchange.
   - **Resolution Actions:** Verified customer's account, confirmed exchange process, clarified return instructions, advised on activation fee and service details.
   - **Required Escalation:** False
   - **Resolved:** True

### Conclusion:

The analysis provides a detailed breakdown of each customer service call, including sentiment, problem statements, actions taken by the agent, the need for escalation, and the resolution status. The results are presented in JSON format for each call, making it easy to understand and process the information.