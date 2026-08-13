# Home Lab: Ticketing System + Active Directory

This is my home lab project where I practice handling real support tickets
and resolving them against my Active Directory domain (ENTERPRIZE.COM). I'm
using a ticketing tool to receive requests and my Windows Server 2025
domain controller to actually fix them.

## My setup

- Ticketing tool: web-based ticket dashboard
- Domain controller: Windows Server 2025 Datacenter, EC2AMAZ-E3K8IDE
- Domain: ENTERPRIZE.COM
- Access method: Remote Desktop Connection

## What I did

### 1. Getting the ticket

![Support ticket](images/01-support-ticket-password-reset.png)

Ticket #12345 came in through the web form, flagged as Negative sentiment,
topic "Unable to reset password." A customer named Arlo Wilson wrote in
saying he'd been trying to log in for 30 minutes, requested a password
reset link three times, and never got an email, even after checking spam.
He'd been a customer for two years and said this had never happened before,
so he wanted it looked at the same day.

### 2. Resolving it in Active Directory

![AD password reset](images/02-ad-password-reset-resolution.png)

I went into Active Directory Users and Computers, found Arlo Wilson's
account under Engineering, and used Reset Password instead of relying on
the self-service email link, since that clearly wasn't going through. I
checked "User must change password at next logon" so he'd set his own new
password on his next login, and confirmed his account wasn't locked out on
the domain controller before closing out the ticket.

## Things I learned

- Self-service password reset emails can fail silently, so it's worth
  checking the account status directly in AD instead of just assuming the
  user did something wrong.
- Forcing a password change at next logon is a good habit when I'm the one
  setting a temporary password, so the user ends up with something only
  they know.
- Checking the Account Lockout Status while I'm already in the reset dialog
  saves a step, since a locked account can look identical to a reset issue
  from the user's side.

## Note

This is just a personal lab for learning. No real company info or
credentials are in here.
