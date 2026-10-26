# ANAQAH ওয়েবসাইট সেটআপ গাইড

## ১) অর্ডার সংরক্ষণ চালু করুন (Google Sheet, বিনামূল্যে, প্রায় ১০ মিনিট)

1. নিজের Gmail দিয়ে https://sheets.google.com এ নতুন একটা Sheet খুলুন, নাম দিন "ANAQAH Orders"।
2. মেনু থেকে **Extensions → Apps Script** চাপুন।
3. সেখানে থাকা কোড মুছে `order-backend.gs` ফাইলের পুরো কোড পেস্ট করুন।
4. কোডের উপরে `SECRET` লাইনে নিজের গোপন পাসকোড লিখুন (এটাই অ্যাডমিন প্যানেলের পাসকোড হবে)। `NOTIFY` ঠিক আছে কি দেখুন।
5. **Deploy → New deployment → Type: Web app** বেছে নিন।
   - Execute as: **Me**
   - Who has access: **Anyone**
6. Deploy চাপুন, Google অনুমতি চাইলে Allow করুন। শেষে একটা **Web app URL** পাবেন (`https://script.google.com/macros/s/.../exec`), এটা কপি করুন।
7. `index.html` খুলে `const ENDPOINT=""` লাইনে ওই URL বসান, যেমন `const ENDPOINT="https://script.google.com/macros/s/XXXX/exec"`।
8. কোড বদলালে Deploy → Manage deployments → Edit → New version দিয়ে আবার Deploy করতে হয়।

এরপর যা হবে:
- কাস্টমার অর্ডার করলেই Sheet-এ নাম, ফোন, জেলা, থানা, ঠিকানা, মোট টাকা জমা হবে এবং `info@anaqahfashion.com` এ ইমেইল যাবে।
- ওয়েবসাইটের নিচে "Staff Portal" বা `আপনার-ডোমেইন/#admin` থেকে পাসকোড দিয়ে ঢুকলে সব অর্ডার দেখা, কল করা, WhatsApp করা, কনফার্ম/ডেলিভারিড/বাতিল করা যাবে। যেকোনো ফোন বা কম্পিউটার থেকেই দেখতে পারবেন।

## ২) ডোমেইনে (anaqah.com) ওয়েবসাইট চালু করা

1. **ডোমেইন কিনুন:** anaqah.com বা anaqah.com.bd নাম আগে থেকে কারও নেওয়া কি না রেজিস্ট্রারে খুঁজে দেখুন, তারপর কিনুন (বছরে কিছু টাকা লাগে)।
2. **হোস্টিং:** ফ্রিতে Netlify, Cloudflare Pages বা Vercel ব্যবহার করতে পারেন। `index.html` এবং `images` ফোল্ডার একসাথে আপলোড করুন (ফোল্ডারের নাম ঠিক `images` থাকতে হবে)।
3. হোস্টিং সাইটের **Custom domain** অপশনে কেনা ডোমেইন যুক্ত করুন, তারা DNS-এ কী বসাতে হবে বলে দেবে।
4. ব্রাউজারে `anaqah.com` লিখলে তখন সাইট খুলবে। Google সার্চে নাম দিয়ে আসতে কয়েক দিন থেকে সপ্তাহ লাগতে পারে। দ্রুত করতে Google Search Console-এ সাইট জমা দিন।

## ৩) ছাড়ার আগে চেকলিস্ট
- `SECRET` পাসকোড বদলানো হয়েছে
- নমুনা রিভিউ বদলে আসল রিভিউ দেওয়া হয়েছে (বা সেকশন সরানো হয়েছে)
- একটা টেস্ট অর্ডার দিয়ে Sheet ও ইমেইলে এসেছে কি দেখা হয়েছে