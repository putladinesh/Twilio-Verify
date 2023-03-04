# Twilio Verify
This module uses the Twilio Verify Service to send One-time Passwords (OTP).

Without the hassle of creating flows in your Mendix app to generate one-time passwords and send them as SMS to users with another service provider, this module simplifies authentication at scale with Verify API.
Validate users via SMS and popular channels such as call and WhatsApp to decrease fraud with a fully-managed API that handles the heavy lifting.

# Dependencies: 
 Encryption Module (https://marketplace.mendix.com/link/component/1011)

# Configuration:

 **Twilio Configuration:**
*	Go to twilio.com and sign up for an account - https://www.twilio.com/try-twilio
*	Copy Account SID and Auth Token
*	Get a Twilio number by clicking the “Get a Twilio Phone Number” button from Twilio console
* To use Verify Service, one should Create a Service SID for Verify. 
*	Go to Twilio Console, Click the Verify Service under Account Security Section, and Click the Blue Color “ + “ icon to Create a new Verify service.  Copy the Service SID and select the Code Length Under the General Section of the service setting. Enable the SMS, WhatsApp, and Voice services by moving next to subsequent tabs.
*	Note: Since the account is new and not billed yet, you will have to Verify the Phone number you want to send the code. You can do it from #Verified phone numbers-> Manage->Verified Caller IDs -> Add a new Caller Id and verify the mobile number you want to send the Secret code.

**Mendix Application Setup:**
* Add the Encryption key value in the Encryption key constant. This key is used to encrypt your Twilio API key
* Go to Use Me->Admin ->Pages-> TwilioSetting and add it to Navigation
* Click new and Enter the below Fields
   - Twilo Login Id
   - Account SID
   - Token
   - Service SID
   - From Phone Number
* These values should be copied from the Twilio console explained in Twilo Configuration section.

**Microflows:**
* SUB_SendVerificationCode is used to send the verification code. The microflow accepts two parameters:
	 - ENU_Channel: The channel via which the code is to be sent
	 - ToNumber: User’s mobile number (Appended with +country code at the start). There should be no space between the number and any other characters like “ – “.
* SUB_ValidateVerificationCode is used to verify the code. The microflow accepts two parameters:
	 - Code : Secret code sent to the user mobile number.
   - ToNumber: User’s mobile number (Appended with +country code at the start). There should be no space between the number and any other characters like “ – “.
* SUB_CreateApiErrorLog is used to save error messages in Database in case of failure of the call.

# Working:
* After saving the Credentials, go to the Examples folder Call the SendVerificationCode page from the navigation.
* Mobile number must be entered with ‘+Countrycode’ followed by the Mobile number and select the channel you wish to send the verification code.  
* Click the SendCode button to send the Verification code. 
* You can place the Response_ErrorLogs page in the navigation to track the Error response. 

# Pricing :
 * Check the Twilio pricing page for pricing details : [Twilio Verify Pricing](https://www.twilio.com/verify/pricing/)


