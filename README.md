# Vapi-Inbound-Outbound-Workflow-

## Overview of Project:
**Inbound flow:**  
Customer will call on vapi number then PropAI Bot voice agent will greet the customer and suggest them to check the available slots for viewing property , If user confirms a date and time then Agent will schedule a viewing date for customer. Agent also check whether a customer is an already existing customer or a new customer.

**Outbound flow:**  
Alex Agent will call on customer number with customer's data such as name, interested property, budget range etc. and based on that agent will suggest available property for customer and book a schedule for viewing property.

At the end when call ends The information will be stored on Google sheet


## API & Configuration 

### Vapi Configuration : 

**1. Phone Number configuration :**

**-> Add OpenAI Provider Key in Vapi**  
- Log in to https://app.vapi.ai
- Go to Settings → Provider Keys
- Add your OpenAI API key

**-> Buy / Import a Phone Number**
- Create account in Twilio buy a number in twilio from free 15$ credits
- Go to Phone Numbers → Create Phone Number -> Import Twilio
- Add your twilio number in Twilio phone number -> Get Account sid and auth token and Paste Your Twilio’s Account SID and Auth token -> give a label name for number -> Import from Twilio
- Copy the Phone Number ID (at top just below the Phone number you will get phone number id) — you'll need it for outbound calls

**-> Set the Server URL (critical for inbound)**
- Go to Phone Numbers → click your number
- Under Server URL, paste your n8n inbound webhook URL: (vapi does not accept localhost url so convert localhost n8n webhook url to public using ngrok by following below steps of ngrok)   
https://abc123.ngrok-free.app/webhook-test/vapi-inbound
- Click Save

**2. Assistant - configuration:**
- Goto Assistant -> Create assistant 
- Copy the assistant id -> You will use it in outbound flow

### Inbound Workflow Configuration :

- Open Google Sheet module
- Create credential of google sheet then select it in n8n google sheet node

### Outbound workflow Configuration : 
**1. Create Outbound Call  node**
- Click on Vapi API – Create Outbound Call  node -> Open It
- Bearer Auth -> Create new credentials -> Enter your Vapi’s private key in Bearer Token -> Save

In Header : 
- Replace Your_vapi_private_key with your actual vapi private key


**2. Build Outbound Call Payload node:**  
- Open Build Outbound Call Payload node
- Replace Your_phone_number_id with your phone_number id
- Replace Your_Assistant_id with your correct assistant_id

#### Vapi Inbound + Outbound Workflow : 
<img width="1518" height="642" alt="image" src="https://github.com/user-attachments/assets/dcff55e8-5f95-4c2e-9a6e-8e62a3570230" />







