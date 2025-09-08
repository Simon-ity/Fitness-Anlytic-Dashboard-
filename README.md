<img width="1445" height="811" alt="Homepage" src="https://github.com/user-attachments/assets/bc84c73c-af93-4011-9a5b-b99e9f3cf69d" />
# Fitness Center Business Intelligence Dashboard

**Power BI Analytics Project | Data Visualization & Business Intelligence**

A comprehensive 3-page Power BI dashboard system analyzing fitness center operations with real-time tracking of 100 clients, 20 trainers, $4.1M revenue performance, advanced health analytics, and detailed member demographics.

##  Project Overview

This comprehensive Power BI project transforms manual fitness center operations into an automated business intelligence solution with integrated health analytics and demographic insights. The dashboard provides real-time insights across **3 interactive pages** managing **100 active clients**, **20 professional trainers**, generating **$4.1M in annual revenue**, plus comprehensive health tracking and detailed member demographics.

## Multi-Page Dashboard System

### **Navigation Menu:**
- **Home** - Executive business overview
- **Insights** - Financial performance analytics  
- **Measurements** - Health metrics and BMI calculations
- **Members** - Demographic analysis and member profiles

## 📈 Page-by-Page Dashboard Features

### **Page 1: Home - Business Performance Dashboard**
- **Client Base:** 100 active members across multiple membership tiers
- **Staff Management:** 20 trainers with performance tracking
- **Financial Performance:** $4.1M revenue, $1.2M expenses, $2.9M profit (70.7% profit margin)
- **Membership Distribution:** Real-time tracking across Platinum, Gold, Silver tiers

### **Page 2: Calculator - Health Analytics Dashboard**
- **BMI Tracking:** Real-time Body Mass Index calculations (45.80 example)
- **Calorie Calculator:** Personalized daily calorie recommendations (1.78K TDEE)
- **Health Metrics:** BMR, TDEE, and weight management calculations
- **Interactive Tools:** Gender, age, height, weight, and activity level inputs

### **Page 3: Members - Demographics & Profile Analytics** *(Featured Page)*
- **Age & Gender Distribution:** Visual breakdown of member demographics
- **Member Status Analysis:** Active vs Expired membership tracking
- **Individual Profiles:** Detailed member information with BMI tracking
- **Goal-based Segmentation:** Muscle Gain, Weight Loss, Maintenance categories

## 👥 Detailed Member Demographics Analysis

### **Age & Gender Distribution Charts:**
**By Gender:**
- **40 to 60 Age Group:** 23 Female, 30 Male (Total: 53 members - largest segment)
- **25 to 40 Age Group:** 14 Female, 18 Male (Total: 32 members)
- **18 to 25 Age Group:** 8 Female, 7 Male (Total: 15 members)

**By Membership Status:**
- **40 to 60 Age Group:** 19 Active, 34 Expired
- **25 to 40 Age Group:** 16 Active, 16 Expired  
- **18 to 25 Age Group:** 9 Active, 6 Expired

### **Comprehensive Member Profiles:**
**Current Active Members:**
1. **Laura Lopez** (Male, 48) - Joined: Sep 25, 2024 | Goal: Muscle Gain | BMI: 26.10 | Progress: 48%
2. **Natasha Wood** (Male, 56) - Joined: Dec 9, 2024 | Goal: Weight Loss | BMI: 22.30 | Progress: 47%
3. **Heather Barr** (Female, 22) - Joined: Jul 23, 2024 | Goal: Muscle Gain | BMI: 34.90 | Progress: 48%
4. **Timothy Duncan** (Male, 40) - Joined: Nov 27, 2024 | Goal: Maintenance | BMI: 22.20 | Progress: 48%
5. **Leslie Wells** (Female, 33) - Joined: Nov 15, 2024 | Goal: Maintenance | BMI: 27.90 | Progress: 50%
6. **Nathan McCormick** (Female, 28) - Joined: Nov 11, 2024 | Goal: Weight Loss | BMI: 29.10 | Progress: 51%

### **Member Analytics Insights:**
- **Primary Age Group:** 40-60 year-olds represent 53% of total membership
- **Gender Distribution:** Slight male majority in most age groups
- **Goal Distribution:** Mixed goals (Muscle Gain, Weight Loss, Maintenance)
- **BMI Range:** 22.20 - 34.90 across active members
- **Average Progress:** ~48% completion rate across active memberships

## 🛠 Advanced Technical Implementation

### **Multi-Page Navigation System:**
- **Bookmarks:** Seamless navigation between Home/Overall/Calculator/Members
- **Consistent Branding:** Professional fitness center theme across all pages
- **Real-time Updates:** 03:01 AM last dashboard update timestamp
- **Interactive Filters:** Gender (Female/Male) toggles for dynamic analysis

### **Demographics Data Model:**
```dax
// Age Group Classification
Age_Group = 
SWITCH(
    TRUE(),
    [Age] >= 18 && [Age] <= 25, "18 to 25",
    [Age] >= 25 && [Age] <= 40, "25 to 40", 
    [Age] >= 40 && [Age] <= 60, "40 to 60",
    "Other"
)

// Member Status Analysis
Active_Members_by_Age = 
CALCULATE(
    COUNTROWS(Members),
    Members[Status] = "Active",
    Members[Age_Group] = SELECTEDVALUE(Age_Groups[Age_Group])
)

// BMI Health Classification
BMI_Category = 
SWITCH(
    TRUE(),
    [BMI] < 18.5, "Underweight",
    [BMI] >= 18.5 && [BMI] < 25, "Normal",
    [BMI] >= 25 && [BMI] < 30, "Overweight", 
    [BMI] >= 30, "Obese"
)

// Goal Distribution Analysis
Goal_Distribution = 
CALCULATE(
    COUNTROWS(Members),
    ALLEXCEPT(Members, Members[Goal])
)
