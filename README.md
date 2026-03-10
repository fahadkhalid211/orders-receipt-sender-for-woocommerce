=== Order Receipts Sender for WooCommerce ===

Contributors: fahadkhalid211

Tags: woocommerce, order receipt, whatsapp, telegram, sms

Requires at least: 5.8

Tested up to: 6.9

Stable tag: 2.1.0

Requires PHP: 7.4

License: GPLv2 or later

License URI: https://www.gnu.org/licenses/gpl-2.0.html

Send WooCommerce order receipts via WhatsApp, Telegram and SMS simultaneously. Includes OTP login and registration verification.

== Description ==

**Order Receipts Sender for WooCommerce** keeps your customers informed the moment their order is placed — by sending a fully customisable receipt straight to their phone via WhatsApp, Telegram, or SMS, in addition to the standard WooCommerce email. The email is never disabled or replaced.

Whether you run a small store or a high-volume shop, the plugin adapts to your scale: start free with Telegram or TextBelt, upgrade to Meta's official WhatsApp Business API or Twilio when you're ready.

---

= Key Features =

**Multi-Channel Order Receipts**

* Send receipts via WhatsApp, Telegram, and SMS — all three simultaneously if you wish.
* Each channel fires independently; a failure on one does not block the others.
* Every send attempt (success or failure) is recorded as an order note in WooCommerce.
* Admin can manually resend a receipt from any order detail page.

**Multiple Providers Per Channel**

* WhatsApp: Choose from UltraMsg, Meta WhatsApp Business API, CallMeBot, or Twilio.
* SMS: Choose from TextBelt (free tier available) or Twilio.
* Telegram: Telegram Bot API — free, no per-message cost, no third-party account needed.

**Fully Customisable Message Templates**

* Separate templates for WhatsApp/Telegram (supports *bold* markdown) and SMS (plain text).
* Rich placeholder system — insert any order detail into your message with simple tags.
* Available placeholders: {customer_name}, {site_name}, {order_number}, {order_date}, {order_status}, {order_items}, {order_total}, {order_url}, {billing_address}.

**OTP Login & Registration Verification**

* Add a one-time password option to the WordPress and WooCommerce login forms.
* Choose whether OTP is optional (alternative to password) or required (blocks password-only login).
* Optionally require phone OTP verification before a new customer can complete registration.
* OTP delivered via SMS, WhatsApp, or Telegram — your choice.
* 6-digit codes expire after 10 minutes; brute-force protected (max 5 attempts).
* Codes stored as hashed values — the plain code is never saved to the database.

**Smart Checkout Fields**

* Adds optional "Phone for WhatsApp/SMS" and "Telegram Chat ID" fields at checkout, shown only when the relevant channel is active.
* Fields are prefilled for returning customers from their saved profile.
* Phone number validated on checkout (E.164 international format, e.g. +358401234567).
* Customer details saved to user meta for a seamless repeat-order experience.

**Built-in Test Sender**

* Test every channel directly from the settings page before going live.
* Enter any recipient and fire a test message — success or error feedback shown instantly.

---

= Provider Overview =

**WhatsApp Providers**

UltraMsg — Free trial, easiest setup. Sign up, scan a QR with WhatsApp, copy Instance ID + Token.

Meta WhatsApp Business API — Official Meta integration. Free up to 1,000 conversations per month. Requires a Facebook Developer App.

CallMeBot — Free for personal/small use. Each recipient must opt in once by messaging CallMeBot directly.

Twilio WhatsApp — Paid, production-grade. Supports high-volume sending with full delivery reporting.

**SMS Providers**

TextBelt — 1 free SMS per day using the default key. Purchase credits at textbelt.com for higher volume.

Twilio SMS — Paid, global reach. Same Twilio credentials as Twilio WhatsApp.

**Telegram**

Always free. Requires only a bot token from @BotFather. No per-message cost, no opt-in required beyond customers sharing their Chat ID.

---

== Installation ==

= Automatic Installation =

1. Log in to your WordPress admin.
2. Go to Plugins → Add New.
3. Search for "Order Receipts Sender for WooCommerce".
4. Click Install Now, then Activate.

= Manual Installation =

1. Download the plugin .zip file.
2. Go to Plugins → Add New → Upload Plugin.
3. Choose the .zip file and click Install Now.
4. Click Activate Plugin.

= After Activation =

1. Go to WooCommerce → Settings → Messaging Receipt.
2. Enable receipts and select your active channel(s).
3. Enter credentials for each channel you want to use (see setup guides below).
4. Customise your message templates.
5. Use the Send Test panel to verify everything is working.
6. Save settings.

---

== Channel Setup Guides ==

= Telegram (Easiest — Recommended for First-Time Users) =

1. Open Telegram and search for @BotFather.
2. Send the command /newbot and follow the prompts to name your bot.
3. BotFather gives you a Bot Token in the format 123456789:AAxxxxxxx. Copy it.
4. Start a conversation with your own bot by searching for it and clicking Start.
5. Visit https://api.telegram.org/bot<YOUR_TOKEN>/getUpdates in your browser to find your Chat ID (look for "id" inside the "chat" object).
6. Paste the Bot Token and your Chat ID (as the Admin/Fallback Chat ID) into the plugin settings.
7. Customers enter their own Chat ID in the Telegram Chat ID field at checkout to receive receipts personally.

= WhatsApp via UltraMsg =

1. Sign up at ultramsg.com.
2. Create a new instance and scan the QR code with the WhatsApp account you want to send from.
3. Copy your Instance ID and Token from the dashboard.
4. Paste them into UltraMsg Credentials in the plugin settings.
5. Select UltraMsg as the WhatsApp provider and enable WhatsApp as an active channel.

= WhatsApp via Meta Business API =

1. Go to developers.facebook.com/apps and create a new app (Business type).
2. Add the WhatsApp product to your app.
3. Under WhatsApp → Getting Started, note your Phone Number ID.
4. Generate a System User Access Token with the whatsapp_business_messaging permission.
5. Paste the Phone Number ID and Access Token into the plugin settings.
6. Select Meta WhatsApp Business API as the WhatsApp provider.

Free tier: 1,000 conversations per month.

= WhatsApp via CallMeBot =

1. Save the number +34 644 61 09 91 in your phone contacts.
2. Send the message "I allow callmebot to send me messages" to that contact on WhatsApp.
3. You will receive an API key by reply within a few minutes.
4. Paste the API key into the plugin settings.
5. Select CallMeBot as the WhatsApp provider.

Note: Each recipient must complete this opt-in step for their own number before they can receive messages.

= SMS via TextBelt =

1. Leave the API Key field blank (or enter "textbelt") to use the free tier (1 SMS/day).
2. For higher volume, purchase credits at textbelt.com and paste your paid key.
3. Select TextBelt as the SMS provider and enable SMS as an active channel.

= SMS or WhatsApp via Twilio =

1. Sign up at twilio.com and get your Account SID and Auth Token from the Console Dashboard.
2. For WhatsApp: note your Twilio WhatsApp-enabled number (e.g. +14155238886).
3. For SMS: note your Twilio SMS-capable phone number.
4. Paste SID, Auth Token, and the relevant from-numbers into the Twilio credentials section.
5. Select Twilio WhatsApp or Twilio SMS as the provider for the respective channel.

Note: Twilio WhatsApp sandbox requires recipients to send a join message first. Use an approved production number for live stores.

---

== OTP Login & Registration ==

= Enabling OTP Login =

1. Go to WooCommerce → Settings → Messaging Receipt → Login OTP Settings.
2. Check Enable OTP Login.
3. Choose whether to also check Require OTP to Login. When checked, password-only login is blocked — customers must use OTP. When unchecked, OTP is an optional alternative to password login.
4. Select your OTP Channel (SMS is recommended for the widest reach).
5. Save settings.

= How OTP Login Works for Customers =

1. The customer visits the WordPress login page or the WooCommerce My Account page.
2. They enter their username or email in the standard field, then enter their phone number (or Telegram Chat ID) in the OTP section and click Send OTP.
3. A 6-digit code is sent to their phone. It is valid for 10 minutes.
4. They type the code into the OTP field and submit the form.
5. If the code matches, they are logged in — no password needed.

= Enabling OTP on Registration =

1. Check Require OTP on Registration in the same settings section.
2. Customers will see a phone/Chat ID field and OTP entry on the WooCommerce registration form.
3. They must successfully verify their phone number before their account can be created.

= OTP Security Notes =

* Codes are 6 digits, generated using WordPress's wp_rand().
* Stored in the database as a wp_hash() — the plain code is never saved.
* Codes expire after exactly 10 minutes.
* After 5 failed attempts the code is locked (brute-force protection).
* Expired codes are cleaned up automatically every hour by WP-Cron.
* All AJAX endpoints are nonce-verified.

---

== Message Template Reference ==

Go to WooCommerce → Settings → Messaging Receipt → Message Templates to customise your messages.

= Available Placeholders =

{customer_name} — Customer's full billing name. Example: John Smith

{site_name} — Your WordPress site name. Example: My Store

{order_number} — WooCommerce order number. Example: 1042

{order_date} — Date the order was placed. Example: March 10, 2026

{order_status} — Current order status (human-readable). Example: Processing

{order_items} — Line-by-line list of all items ordered with quantities and prices.

{order_total} — Total order value with currency symbol. Example: $58.00

{order_url} — Full URL link to the customer's order detail page.

{billing_address} — Customer's formatted billing address as plain text.

= Formatting Tips =

* Use *text* (asterisks) for bold formatting in WhatsApp and Telegram messages.
* Emoji are fully supported in the WhatsApp/Telegram template.
* Keep the SMS template under 160 characters to avoid messages being split and billed as two.
* The SMS template strips all markdown — asterisks are removed automatically.

---

== Frequently Asked Questions ==

= Does this plugin disable the default WooCommerce email? =

No. WooCommerce emails fire exactly as they always have. This plugin sends messaging receipts in addition to the email — it never replaces or suppresses email.


= Which channel should I start with? =

Telegram is the easiest to set up (free, 2 minutes, no customer opt-in required beyond sharing their Chat ID at checkout). For wider reach without needing a Chat ID, try SMS via TextBelt for testing or Twilio for production.


= Can I send on multiple channels at once? =

Yes. Tick all the channels you want under Active Channels. Every enabled channel receives the receipt simultaneously for each qualifying order. A failure on one channel is logged as an order note but does not affect the others.


= When is the receipt sent? =

By default, when the order reaches Processing status (after successful payment). You can change this to Pending Payment, On Hold, or Completed in the Trigger on Status setting.


= What if a customer does not provide a WhatsApp number or Telegram Chat ID? =

For WhatsApp and SMS, the plugin falls back to the WooCommerce billing phone number. For Telegram, it falls back to the Admin/Fallback Chat ID you set — so you still get notified.


= Can I manually resend a receipt? =

Yes. Open any order in WooCommerce → Orders, click the Order Actions dropdown (top right of the order detail page), select Resend Messaging Receipt, and click the arrow button to run it.


= What phone number format should customers use? =

International E.164 format with a + prefix — for example +358401234567 or +12025550123. The checkout field validates this format automatically and shows an error if it is incorrect.


= Can I use OTP login without making it mandatory? =

Yes. Enable OTP Login but leave Require OTP to Login unchecked. Customers can then choose either their password or OTP — both methods will work.


= Does the plugin create any database tables? =

Yes, one table: {prefix}orm_otps. It stores temporary hashed OTP codes and is created automatically on plugin activation. Expired entries are cleaned up hourly. The table is not dropped on deactivation (to preserve any pending data across upgrades).



= Is this plugin compatible with WooCommerce HPOS? =

Yes. Order data is accessed via standard WooCommerce CRUD methods ($order->get_meta(), $order->get_billing_phone(), etc.), which are fully compatible with both the legacy posts-based storage and the new High-Performance Order Storage.


= I receive the test message but customers do not. What is wrong? =

The most common cause is a missing recipient value. Check that:
1. The customer has provided a phone number or Chat ID at checkout.
2. The correct checkout field is active in the plugin settings (WhatsApp/SMS requires billing_whatsapp; Telegram requires billing_telegram_chat_id).
3. The phone number is in E.164 format.
Check the order notes — they show exactly which channels were attempted and any error returned by the API.


= Where can I report bugs or request features? =

Open an issue at https://github.com/fahadkhalid211/


---

== Screenshots ==

1. Settings — General & Active Channels: enable receipts, choose trigger status, select channels.
2. Settings — WhatsApp Provider: choose your provider and enter credentials.
3. Settings — Telegram: enter Bot Token and Admin/Fallback Chat ID.
4. Settings — Message Templates: customise WhatsApp/Telegram and SMS templates with placeholder tags.
5. Settings — OTP Login: configure OTP verification for login and registration.
6. Settings — Test Sender: test each channel independently with a live test message.
7. Checkout — Custom Fields: WhatsApp/SMS phone and Telegram Chat ID fields.
8. Login Form — OTP Section: OTP identifier input and Send OTP button below the standard form.
9. Order Detail (Admin) — messaging contact info and receipt send status.
10. Order Notes — automatic success/failure notes added per channel after each send attempt.

---

== Changelog ==

= 2.1.0 =
* Added: Require OTP to Login setting — enforce OTP and block password-only login.
* Added: OTP fields and asset enqueue on WooCommerce My Account login form.



= 2.0.0 =
* Complete rewrite: multi-channel simultaneous sending (WhatsApp, Telegram, SMS).
* Multiple providers per channel: UltraMsg, Meta WABA, CallMeBot, Twilio, TextBelt.
* OTP login and registration verification.
* Customisable message templates with placeholder system.
* Per-channel test message sender in admin settings.
* Order notes for every send attempt.
* Admin/Fallback Chat ID for Telegram.

= 1.0.0 =
* Initial release with basic WhatsApp (CallMeBot / Twilio) order receipt sending.

---

== Upgrade Notice ==

= 2.1.0 =
After upgrading, please deactivate and reactivate the plugin once to ensure the OTP database table is created with the correct schema. This is a one-time step.
