# Task 1 - GTM Event Schema

## Objective

To implement Google Tag Manager (GTM) event tracking for the OrthoNow website so that all important user interactions are captured in Google Analytics 4 (GA4) for reporting, conversion tracking, and marketing optimization.

## GTM Event Schema

| Event Name | Trigger Type | Key Parameters | GA4 Report / Audience |
|------------|--------------|----------------|-----------------------|
| appointment_step_1 | Form Step Completion | clinic_location, specialty, page_name | Funnel Exploration |
| appointment_step_2 | Form Step Completion | patient_name, phone_number, preferred_date | Funnel Exploration |
| appointment_completed | Form Submission | booking_id, clinic_location, specialty | Conversions |
| call_now_clicked | Button Click | page_name, clinic_location, phone_number | Engagement Report |
| whatsapp_clicked | Click on WhatsApp Button | page_name, device_type, source | Engagement Report |
| patient_guide_downloaded | Form Submit + PDF Download | guide_name, patient_name, phone_number | Downloads Report |
| clinic_page_view | Page View | clinic_name, city, page_url | Pages & Screens |
| blog_scroll_90 | Scroll Depth (90%) | article_title, scroll_percentage, category | Engagement Report |

## Booking Funnel Tracking

The appointment booking form consists of three steps. Each completed step pushes a custom event to the dataLayer. Google Tag Manager (GTM) listens for these custom events and sends them to Google Analytics 4 (GA4). Using these events, a Funnel Exploration report can be created in GA4 to identify where users drop off before completing their appointment booking.

### Booking Funnel

Step 1 → Select Clinic & Specialty

↓

Step 2 → Enter Name, Phone & Preferred Date

↓

Step 3 → Confirm Appointment

↓

Booking Completed

window.dataLayer = window.dataLayer || [];

window.dataLayer.push({
  event: "booking_step_complete",
  step_number: 1,
  step_name: "location_specialty_selected",
  clinic_location: "Bengaluru",
  specialty: "Orthopaedics"
});


window.dataLayer.push({
  event: "booking_step_complete",
  step_number: 2,
  step_name: "patient_details_entered",
  patient_name: "Hemant Rana",
  phone_number: "9876543210",
  preferred_date: "2026-07-10"
});


window.dataLayer.push({
  event: "booking_completed",
  step_number: 3,
  booking_status: "Confirmed",
  clinic_location: "Bengaluru",
  specialty: "Orthopaedics"
});


## Google Ads Conversion

### Selected Conversion Event

**Event Name:** appointment_completed

### Reason

The **appointment_completed** event represents a successful consultation booking and directly reflects the primary business goal of the campaign. Importing this event into Google Ads enables Smart Bidding to optimize for high-quality leads rather than intermediate actions like button clicks or page views. This helps improve campaign performance and maximize return on ad spend (ROAS).