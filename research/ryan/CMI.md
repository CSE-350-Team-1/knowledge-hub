---
title: Similar Offerings and CMI Research
last updated: 5/26/2026
tags: research, competitive-analysis, grocery-list, CMI
summary: Analysis of similar grocery list applications including Listonic, Bring!, and generic note-taking tools, covering general characteristics, development practices, and shortfalls relevant to our project.
---

# overview
This document surveys existing grocery list and shopping management applications to inform the design of our grocery list service. Three categories are examined: dedicated grocery list apps (Listonic, Bring!), and generic note-taking apps repurposed for shopping.

# Listonic Analysis
Listonic is a dedicated grocery list app with over 20 million users, available on iOS, Android, and web. Its core value proposition is speed and organization. Users can create lists quickly, share them in real time, and have items automatically sorted by store aisle or category. Key features include:
 - Real-time list syncing across devices and collaborators
 - Automatic item sorting by store aisle or category (produce, dairy, etc.)
 - Smart autocomplete that learns from shopping history
 - Voice input for hands-free item entry
 - Per-item price tracking with running total calculation
 - Pantry management and recipe keeper

Development Analysis:
Their known tech stack from client projects includes Kotlin and Jetpack Compose for Android, Swift and SwiftUI for iOS, with TeamCity, Octopus, AWS, Azure, Docker, and Firebase on the infrastructure side. 
Their development philosophy is user-centric, with emphasis on onboarding design, smart feature discovery, and iterative UX improvements — having shipped roughly 100+ versions of the app. (https://dev.listonic.com/listonic-case)

Listonic is free with all core features unlocked; an optional premium tier removes ads.

Criticisms:
 - The cumulative shopping list does not allow deletion or editing of items once added, a noted user complaint
 - Pantry and recipe features are secondary to the core list UX and feel underdeveloped compared to dedicated meal planning apps (trying to do too much?)
 - No meaningful social or discovery features — collaboration is limited to explicit list sharing with known contacts

# Bring Analysis
Bring! (by Bring! Labs AG) takes a more visual, icon-first approach to grocery lists, representing items as image tiles rather than plain text. It has over 13 million downloads and is available on iOS, Android, Wear OS, Apple Watch, and web. Key features include:
 - Visual tile-based UI (icons/photos per item) instead of text lists
 - Real-time shared lists for households and groups
 - Smart search with personalized product recommendations
 - Loyalty card wallet built into the app

Development Analysis:
A 2017 news item references Bring! incorporating machine learning and voice recognition into the app — that's the earliest sourced reference to their ML investment.
Bring! supports voice control via Amazon Alexa and Siri for hands-free item entry. However, Google Assistant support for third-party list apps was dropped, leaving Android users without a voice option until an alternative is provided. (https://www.getbring.com/en/home)

Criticisms:
 - Category customization is limited; users cannot easily restructure preset categories to match their specific store layout
 - No recipe-to-list pipeline or PDF recipe attachment, limiting meal planning use cases
 - Collaboration is household-oriented; no support for more complex group structures (e.g. shared apartments with different budgets)

