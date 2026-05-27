# Incomplete Tasks

## Reconnect Contact Form to n8n

The n8n automation workflow is fully built and ready — it just needs to be reconnected once the n8n plan is upgraded.

**Why it's disconnected:** n8n cloud execution limit was reached. Form was temporarily reverted to Web3Forms so submissions still work.

**To reconnect:**
1. Upgrade n8n plan at `app.n8n.cloud/account/change-plan`
2. In `index.html`, find the `handleSubmit` function and make two changes:

   Change the fetch call from:
   ```js
   const response = await fetch('https://api.web3forms.com/submit', {
     method: 'POST',
     headers: { 'Accept': 'application/json' },
     body: formData
   });
   ```
   To:
   ```js
   const payload = Object.fromEntries(formData.entries());
   const response = await fetch('https://ercole.app.n8n.cloud/webhook/contact-form', {
     method: 'POST',
     headers: { 'Content-Type': 'application/json', 'Accept': 'application/json' },
     body: JSON.stringify(payload)
   });
   ```

3. Remove the four Web3Forms hidden inputs at the top of the form (`access_key`, `subject`, `from_name`, `botcheck`)
4. Commit and push

**n8n Workflow:** "Website Contact Form → Google Sheets + Auto-Reply" (ID: `MXCF6CjwOFY6FBCn`)
- Webhook → appends row to Google Sheet (`15m8nv1dLwgab4zMI9PHWgNCc_TuFnepaykeYGDGuhBc`)
- Sends Gmail auto-reply from `justin.ercole@gmail.com`
- Google Sheet columns: `Submission Date | First Name | Last Name | Email | Inquiry | Message`
