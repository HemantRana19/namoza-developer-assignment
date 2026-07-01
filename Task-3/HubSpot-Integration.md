# Task 3 – HubSpot CRM Integration Strategy

## Objective

Design a scalable strategy to capture consultation form submissions from the landing page and automatically create or update contacts in HubSpot CRM while preserving attribution data and preventing duplicate records.

## Data Flow

Landing Page Form

↓

JavaScript Validation

↓

window.dataLayer.push()

↓

Google Tag Manager (GTM)

↓

HubSpot Form API

↓

HubSpot CRM

↓

Marketing Automation

## Field Mapping

| Landing Page Field | HubSpot Property |
|--------------------|------------------|
| Full Name | First Name |
| Phone Number | Phone |
| Preferred Clinic | Preferred Clinic |
| UTM Source | Original Source |
| UTM Medium | Latest Source |
| UTM Campaign | Campaign |
| Submission Time | Create Date |

## Duplicate Prevention

HubSpot automatically identifies duplicate contacts using the phone number. Before creating a new contact, the integration checks whether the phone number already exists in the CRM. If a matching contact is found, the existing record is updated instead of creating a duplicate.

## UTM Tracking

The landing page captures UTM parameters from the URL and stores them along with the lead.

Example:

utm_source=google

utm_medium=cpc

utm_campaign=orthopaedic_consultation

These values are sent to HubSpot to measure campaign performance and lead attribution.

## Lead Lifecycle

Visitor

↓

Form Submitted

↓

Lead Created in HubSpot

↓

Sales Follow-up

↓

Appointment Confirmed

↓

Customer

## Integration Process

1. The user fills out the consultation form.
2. Client-side validation checks the required fields.
3. The form submission triggers a `window.dataLayer.push()` event.
4. Google Tag Manager captures the event.
5. GTM forwards the lead data to the HubSpot Forms API.
6. HubSpot creates a new contact or updates an existing one.
7. The contact is enrolled in follow-up workflows for appointment confirmation.

## Error Handling

- Validate all required fields before submission.
- Display user-friendly error messages for invalid input.
- If the HubSpot API is unavailable, log the error and allow the user to retry.
- Prevent duplicate form submissions by disabling the submit button while processing.

## Security Considerations

- Use HTTPS for all API requests.
- Never expose private HubSpot API keys in client-side JavaScript.
- Validate and sanitize all user input.
- Store only the minimum required customer information.

## Benefits

- Centralized lead management
- Automatic lead capture
- Campaign attribution using UTM parameters
- Reduced duplicate records
- Faster sales follow-up
- Better reporting and analytics

## Conclusion

This integration ensures that every consultation request is automatically tracked, attributed, and synchronized with HubSpot CRM. The proposed approach supports scalable lead management, accurate marketing attribution, and an improved patient experience while following security and data management best practices.

