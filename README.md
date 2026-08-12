# Microsoft Entra ID — Self-Service Password Reset (SSPR)

 The fourth lab in a 5-parts series.
 A thorough walk through on how to configure and review **Self-Service Password Reset (SSPR)** in Microsoft Entra ID. In this exercise, you will enable SSPR for a specific group, configure authentication methods, require users to register for SSPR, and configure password reset notifications.

> **Estimated completion time:** 15 minutes

---

## 🎯 Objectives

By completing this exercise, you will learn how to:

* Enable **Self-Service Password Reset (SSPR)** for a specific group.
* Configure the authentication methods users can use to reset their passwords.
* Configure SSPR registration requirements.
* Configure password reset notifications.
* Understand the different SSPR configuration scopes and options.

---

## Prerequisites

Before starting, ensure you have:

* Access to a Microsoft Entra tenant.
* Sufficient permissions to configure SSPR.
* Access to the **Project23** group created in a previous exercise.

---

# Task 1 — Configure SSPR for a Specific Group

In this task, you will configure SSPR so that only members of the **Project23** group can use the self-service password reset feature.

### Step 1 — Open Microsoft Entra admin center

Open:

[Microsoft Entra admin center](https://entra.microsoft.com/?utm_source=chatgpt.com)

Sign in using the credentials for your tenant.

---

### Step 2 — Navigate to Password Reset

From the left-hand navigation menu:

1. Select **Protection**.
2. Select **Password reset**.

Locate the **Self service password enabled** setting.

### SSPR Scope Options

| Value        | Description                                         |
| ------------ | --------------------------------------------------- |
| **None**     | No users can use the SSPR feature.                  |
| **Selected** | Only members of the selected group(s) can use SSPR. |
| **All**      | All users can use the SSPR feature.                 |

---

### Step 3 — Enable SSPR for Project23

Configure the setting as follows:

1. Set **Self service password enabled** to **Selected**.
2. Select **No groups selected**.
3. Select the **Project23** group.
4. Select **Select** to confirm your choice.
5. Select **Save**.

### Expected Configuration

```text
Self service password enabled: Selected
Group:                         Project23
```

> **💡 Tip:** Using the **Selected** option allows you to pilot SSPR with a specific group before expanding the feature to the entire organization.

---

# Subtask 1 — Configure SSPR Authentication Methods

SSPR requires users to verify their identity before they can reset their password.

### Step 1 — Open Authentication Methods

Within **Password reset**, select:

**Authentication methods**

---

### Step 2 — Configure Required Methods

Set:

**Number of methods required to reset** → `1`

This determines how many authentication methods a user must successfully complete before they can reset their password.

> **⚠️ Important:** A user's password itself is not considered an authentication method for SSPR verification.

---

### Step 3 — Select Available Methods

Under **Methods available to user**, enable:

* **Email**
* **Mobile phone**
* **Mobile app code**

If you choose to use **Security Questions**, additional configuration is required to specify how many questions users must create and answer.

---

### Step 4 — Save

Select **Save** at the top of the page.

Your authentication configuration should now resemble:

| Setting                   | Value       |
| ------------------------- | ----------- |
| Methods required to reset | **1**       |
| Email                     | **Enabled** |
| Mobile phone              | **Enabled** |
| Mobile app code           | **Enabled** |

---

# Subtask 2 — Configure SSPR Registration

SSPR registration allows users to register their authentication information before they need to perform a password reset.

### Step 1 — Open Registration

Within **Password reset**, select:

**Registration**

---

### Step 2 — Require User Registration

Configure the following settings:

| Setting                                                  | Value       |
| -------------------------------------------------------- | ----------- |
| **Require users to register when signing in?**           | **Yes**     |
| **Number of days before users are asked to re-confirm…** | **90 days** |

---

### Step 3 — Save

Select **Save** to apply the configuration.

### Expected Configuration

```text
Require users to register:       Yes
Re-confirmation interval:        90 days
```

> **💡 Why this matters:** Requiring periodic confirmation helps ensure that users' registered authentication information remains current.

---

# Subtask 3 — Configure SSPR Notifications

Notifications can help users and administrators identify password reset activity.

### Step 1 — Open Notifications

Within **Password reset**, select:

**Notifications**

---

### Step 2 — Configure Notification Settings

Configure the following:

| Setting                                                       | Value   |
| ------------------------------------------------------------- | ------- |
| **Notify users on password reset?**                           | **Yes** |
| **Notify all admins when other admins reset their password?** | **Yes** |

Leave **Notify users on password reset?** at its default value of **Yes**.

---

### Step 3 — Save

Select **Save** to apply the notification configuration.

---

# 📋 Final Configuration Summary

After completing the exercise, your SSPR configuration should contain the following settings:

| Configuration                              | Value     |
| ------------------------------------------ | --------- |
| **SSPR enabled for**                       | Selected  |
| **SSPR group**                             | Project23 |
| **Methods required to reset**              | 1         |
| **Email**                                  | Enabled   |
| **Mobile phone**                           | Enabled   |
| **Mobile app code**                        | Enabled   |
| **Require user registration**              | Yes       |
| **Registration re-confirmation**           | 90 days   |
| **Notify users after password reset**      | Yes       |
| **Notify admins of admin password resets** | Yes       |

---

# ✅ Exercise Checklist

### SSPR Scope

* [ ] Opened **Protection → Password reset**
* [ ] Set SSPR scope to **Selected**
* [ ] Selected the **Project23** group
* [ ] Saved the configuration

### Authentication Methods

* [ ] Opened **Authentication methods**
* [ ] Set required methods to **1**
* [ ] Enabled **Email**
* [ ] Enabled **Mobile phone**
* [ ] Enabled **Mobile app code**
* [ ] Saved the configuration

### Registration

* [ ] Opened **Registration**
* [ ] Enabled **Require users to register when signing in**
* [ ] Set the re-confirmation period to **90 days**
* [ ] Saved the configuration

### Notifications

* [ ] Opened **Notifications**
* [ ] Confirmed user password-reset notifications are enabled
* [ ] Enabled notifications for administrators when other administrators reset their passwords
* [ ] Saved the configuration

---

## 🧠 Key Takeaways

**Self-Service Password Reset (SSPR)** allows users to securely reset forgotten or compromised passwords without requiring an administrator to manually reset them.

Key configuration areas include:

* **Scope** — Determines which users can use SSPR.
* **Authentication methods** — Defines how users prove their identity before resetting a password.
* **Registration** — Controls whether users must register their authentication information and how frequently they must reconfirm it.
* **Notifications** — Provides users and administrators with visibility into password reset activity.

Using a selected group such as **Project23** is also a useful approach for **testing or piloting SSPR before enabling it more broadly across an organization**.
