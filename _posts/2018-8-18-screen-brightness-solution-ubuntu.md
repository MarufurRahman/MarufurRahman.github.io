---
layout: post
title: উবুন্টুতে Screen Brightness সমস্যার সমাধান
---
উবুন্টুতে স্ক্রিন ব্রাইটনেস (বাড়ানো-কমানো) নিয়ে কোন সমস্যা হলে আশা করি এই সমাধান কাজে লাগবে।
টার্রমিনাল ওপেন করে এই কমান্ডটি দিন।
{% highlight bash %}
ls /sys/class/backlight/
{% endhighlight %}

যদি আপনার গ্রাফিক্স কার্ড Intel হয়ে থাকে তাহলে intel_backlight দেখাবে। 
এরপর নিচের কমান্ডটি দিন।
{% highlight bash %}
sudo touch /usr/share/X11/xorg.conf.d/20-intel.conf
{% endhighlight %}

এরপর এই কমান্ডটি দিন।
{% highlight bash %}
sudo gedit /usr/share/X11/xorg.conf.d/20-intel.conf
{% endhighlight %}

Gedit এডিটরে একটা ফাইল ওপেন হবে যদি না হয় তাহলে আপনার সেখানে যেকোনো এডিটরের নাম কমান্ডের gedit এর জায়গায় লিখে দিন।
নিচের লাইন গুলো কপি করে পেস্ট করুন।
{% highlight bash %}
Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"
EndSection
{% endhighlight %}

এখন ফাইল সেভ করে কম্পিউটার রিস্টার্ট দিন। আশা করি সমাধান হবে।