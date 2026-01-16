# Reflection: Data Privacy & Confidentiality (Focus Bear)

## Research & Learning
* **Key Takeaways from Focus Bear’s Policy:**
    * **Data Minimization:** Focus Bear only collects what is strictly necessary (e.g., email for account, app usage for habit tracking).
    * **No Selling Data:** They explicitly state they do not sell or trade personal information to third parties.
    * **User Control:** Users have the right to access, correct, or delete their data at any time.
    * **Third-Party Services:** They use trusted partners (like Stripe for payments) so that sensitive financial data never hits Focus Bear's own servers directly.
* **Types of Confidential Data:** This includes User PII (email, names), user habit logs, blocked app/website lists, internal source code, and administrative credentials.
* **Best Practices:** Use strong, unique passwords with MFA; never share sensitive data over unencrypted channels; and always follow the "Principle of Least Privilege."
* **Breach Response:** If I suspect a data leak, I will immediately notify the team lead and document the time and nature of the exposure to help with the official investigation and user notification process.

## Reflection
* **Daily Security Steps:** Since I enjoy working in cafes, I must be extra vigilant. I will use a VPN on public networks and ensure my screen is not visible to others when viewing internal logs or user data.
* **Safe Handling:** I will store all work-related documents in the designated company cloud storage rather than my personal local drive. I will use secure password managers to handle any necessary credentials.
* **Common Mistakes:** Including real user emails or API tokens in GitHub Issue descriptions is a frequent error. I will always use "placeholder" data (e.g., `testuser@example.com`) in my bug reports.

## Task Implementation
* **Security Habit:** I will implement a **"Public Workspace Protocol"**: Always locking my computer when stepping away (even for a moment) and using a privacy screen filter if working in crowded environments.
* **Key Learning:** I learned that Focus Bear adheres to high standards like the **GDPR** and **Australian Privacy Principles**. As a QA intern, my testing should verify that data deletion requests actually remove data across all relevant systems.