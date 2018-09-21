# সাইকিট-লার্নে আইরিস ডাটাসেট

আমরা কি কি করবো?

{% hint style="info" %}
১. আইরিস ডাটাসেটের ভেতরে কি আছে? এটা কেন সুপারভাইজড সমস্যা? 

২. সাইকিট-লার্ন এ আইরিস ডাটাসেটকে কিভাবে নেব? 

৩. আমাদের ডাটাসেটকে মেশিন লার্নিং এর ভাষায় সংজ্ঞায়িত করা 

৪. সাইকিট-লার্ন এর ভাষায় আমাদের ডাটাসেটকে কিভাবে আনবো?
{% endhint %}

আরেকটা গল্প দিয়ে শুরু করি বরং। আমাদের এক বন্ধু আইরিস ফুল এর ভক্ত। ওকে একটা ডাটাসেট দেয়া হল। ওই আইরিস ডাটাসেটে তিন ধরনের আইরিস ফুল আছে। সেই তিন ধরণ মানে তিন প্রজাতি। সেগুলোর কিছু মাপজোকও রয়েছে ওখানে। প্রতিটা ফুলের পাপড়ি আর বৃত্তাংশের দৈর্ঘ্য ও প্রস্থ নিয়ে আমাদের এই ডাটা সেট। মাপগুলোই আমাদের একেকটা 'ফিচার'। মেশিন লার্নিং এর ভাষায় "ফিচার"। সামনে ছবি দেখলেই বুঝবেন কি বলেছি আমি। 

{% hint style="info" %}
সামনের চ্যাপ্টারে "এক্সপ্লোরেটোরি ডাটা অ্যানালাইসিস" করার সময় নিজের চোখে ডাটা দেখলে খোলাসা হবে বেশি। 
{% endhint %}

দেখা গেছে, এই আইরিস ফুলের পাপড়ি আর বৃত্তাংশের দৈর্ঘ্য এবং প্রস্থ এর মধ্যে একটা কো-রিলেশন আছে। এর মানে হচ্ছে, আইরিস ফুলের বিভিন্ন প্রজাতির মধ্যে তার পাপড়ি আর বৃত্তাংশের দৈর্ঘ্য এবং প্রস্থের একটা সংযোগস্থল আছে। আমাদের ডাটা সেট এ আইরিস ফুলের তিন প্রজাতির ১৫০টা রেকর্ড আছে। মেশিন লার্নিং এর ভাষায় এই প্রজাতিগুলো হচ্ছে 'টার্গেট ভ্যারিয়েবল'। আমাদের 'টার্গেট ভ্যারিয়েবল' হচ্ছে একটা। এর মধ্যে তিন প্রজাতির নাম। এই তিন প্রজাতির ইংরেজি নাম হচ্ছে ‘সেটোসা’, ‘ভার্সিকালার’ আর ‘ভার্জিনিকা’। এই প্রজাতিগুলোর পাপড়ি মানে ইংরেজিতে ‘পেটাল’ আর বৃত্তাংশ মানে ‘সিপাল’ হিসেবেই ব্যবহার করব এই বইয়ে। এতে ভবিষ্যৎ পড়াশোনাতে কানেক্ট করতে পারবেন সহজে। এখানে প্রতিটা ফুলের সিপাল আর পেটাল এর দৈর্ঘ্য এবং প্রস্থ মিলে মোট ডাটা হয় চারটা।

মনে রাখবেন, চারটা ফিচার

১. পেটাল দৈর্ঘ্য 

২. পেটাল প্রস্থ 

৩. সিপাল দৈর্ঘ্য 

৪. সিপাল প্রস্থ

সবগুলো ডাটা দেয়া আছে সেন্টিমিটারে। এখন আসি সমস্যায়। প্রেডিকশনে। প্রতিটা প্রজাতির আলাদা করে মাপ থাকার ফলে নতুন একটা প্রজাতির ফুলের মাপ যদি আপনাকে দেয়া হয়, তাহলে কি আপনি তার প্রজাতি বের করতে পারবেন? সহজ প্রশ্ন। আপনাকে মাপ দিলে আপনি কি তার প্রজাতি বের করতে পারবেন কি না? ছবি দেখুন। 

![&#x986;&#x987;&#x9B0;&#x9BF;&#x9B8; &#x9A1;&#x9BE;&#x99F;&#x9BE;&#x9B8;&#x9C7;&#x99F;&#x9C7;&#x9B0; &#x9AE;&#x9C7;&#x9B6;&#x9BF;&#x9A8; &#x9B2;&#x9BE;&#x9B0;&#x9CD;&#x9A8;&#x9BF;&#x982; &#x9A8;&#x9BE;&#x9AE; ](../.gitbook/assets/iris%20%281%29.png)

ঠিক বলেছেন। অবশ্যই পারা যাবে! কারণ ওই ফুলগুলোর পেটাল এবং সিপালের দৈর্ঘ্য ও প্রস্থ এর মধ্যে সম্পর্ক বের করতে পারলে সম্ভব সেটা। তার মানে হচ্ছে - শুধুমাত্র মাপগুলো দিলে যেকোন প্রজাতির নাম বের করা সম্ভব। এখন আমাদের কাজ হবে একটা মেশিন লার্নিং মডেল তৈরি করা, যা শিখবে আমাদের দেয়া ১৫০টা রেকর্ড থেকে। শেখার পর আমাদের মডেলকে ‘পেটাল’ এবং ‘সিপালে’র দৈর্ঘ্য প্রস্থ দেয়া হলে সেটা বলতে পারতে হবে কোন প্রজাতির ফুল সেটা।

{% hint style="info" %}
হতাশ হবেন না। সামনে ডাটা নিয়ে নাড়াচাড়া করলে বোঝা যাবে সবকিছু। সত্যি বলছি! আমি নিজেও ডাটাতে কাজ না করা পর্যন্ত বুঝিনি। 
{% endhint %}

আমাদের কাছে যেহেতু তিনটা প্রজাতির ঠিক ঠিক ১৫০টা রেকর্ডে তার সিপাল এবং পেটাল এর দৈর্ঘ্য প্রস্থ আছে, সে কারণে এটা একটা ‘সুপারভাইজড’ লার্নিং মডেল। এই মডেলে অনেকগুলো প্রেডিকটর ভ্যারিয়েবল \(যাকে আমরা 'ফিচার' বলেছি আগে\) আর একটা 'টার্গেট ভ্যারিয়েবল' থাকে। ফুলের সিপাল এবং পেটাল এর দৈর্ঘ্য প্রস্থ আমাদের 'ফিচার'। আগেই দেখেছেন - মোট চারটা ফিচার। আমাদের এক টার্গেট ভ্যারিয়েবলে তিন ক্যাটেগরির প্রজাতি আছে। তাই যেহেতু আমাদেরকে তিনটা প্রজাতির মধ্যে যেকোন একটা প্রজাতিকে বের করতে হচ্ছে, সে কারণে এটা একটা ‘ক্লাসিফিকেশন’ সমস্যা। 

আমাদের ডাটা সেটে প্রতিটা আইরিস ফুলের দৈর্ঘ্য প্রস্থ কিন্তু এই তিনটি প্রজাতির মধ্যেই সীমাবদ্ধ। ১৫০টা ডাটা রেকর্ডে প্রতিটা দৈর্ঘ্য প্রস্থের পাশাপাশি তার উত্তর হিসেবে ঠিক প্রজাতির নাম দেয়া আছে। আগেই বলেছি যেহেতু মাপের সাথে তার প্রজাতির নাম দেয়া আছে, সেকারণে এটি 'সুপারভাইজড' মডেল। একে আমরা ‘লেবেলড’ ডাটা বলতে পারি। মাপের সাথে লেবেল করা আছে প্রতিটা প্রজাতির নাম। চারটা মাপের ফিচার থেকে বের করা হয়েছে একটা 'লেবেলড' টার্গেট ভ্যারিয়েবল। 

{% hint style="info" %}
ক্লাসিফিকেশন: যেখানে টার্গেট ভ্যারিয়েবল মানে উত্তর হচ্ছে ক্যাটেগরিতে। হ্যাঁ অথবা না, কয়েক ধরণের প্রজাতি, পুরুষ না মহিলা।  

রিগ্রেশন: যেখানে টার্গেট ভ্যারিয়েবল ক্যাটেগরি নয়, ক্রমমানের কিছু ভ্যালু। যেমন, বয়স, বেতন।   
{% endhint %}

অনেক গল্প দিলাম, এখন ডাটা দেখার পালা। সত্যি বলতে, ডাটা না দেখলে কেউ বুঝবে না। দেখতে হবে নিজ চোখে। সেজন্য পরের চ্যাপ্টারটা খুব দরকারি। সাইকিট-লার্ন, নামপাই, পান্ডাজ ব্যবহার করতে হবে প্রতিদিন।  সামনের চ্যাপ্টারটা বুঝলে আপনার 'ফাউন্ডেশন' শক্ত হয়ে যাবে। কেউ নড়াতে পারবে না। 

আমাদের সাইকিট-লার্ন লাইব্রেরির ভেতরেই দেয়া আছে এই আইরিস ডাটাসেট। আমাদেরকে খুঁচিয়ে দেখতে হবে কি কি ডাটা আছে? কেমন ধরণের ডাটা? আগে যে গল্প দিলাম তার সাথে যোগসূত্র কোথায়? এই ডাটা দেখার একটা নাম আছে। এক্সপ্লোরেটোরি ডাটা অ্যানালাইসিস। সংক্ষেপে ‘ইডিএ’।
