---
layout: post
title:  "วิธีแก้ Linux Plank error Only X11 environments are supported"
categories: blog
---
*Solving plank only x11 env are not supported problem linux for debian version 10 or gather*

![](https://miro.medium.com/max/2732/1*MBC8pmldXquVIgBJxO3gjA.png){: .img-fluid}

> ถ้าคุณเจอปัญหาเมื่อรัน Plank แล้ว error ว่า Only X11 environments are supported ละก็ บทความนี้มีคำตอบให้คุณนะค้าบ! 😆

## อธิบาย (Explain) ❓
สำหรับคนที่ไม่รุ้ว่ามันมายังไงนะครับคือ Plank เนี่ยเป็นโปรแกรมที่ต้องทำงานกับเครื่องมือจัดการการแสดงผล GDM (GNOME Display Manager) ซึ่ง Plank รองรับแค่ X11 ท่านั้น (X11 หรือ X Window System เป็นระบบการแสดงผลแบบเก่า)ซึ่งใน debian version 10 หรือสูงกว่าได้เปลี่ยนไปใช้ Wayland แทนแล้วเลยเกิดปัญหานี้ขึ้น

## วิธีแก้ไข (solving) 👇
เพียงแค่ทำการเอาคอมเมนต์(#)ใน /etc/gdm3/daemon.conf ตรง WaylandEnable=false ออกเพื่อบังคับให้มันใช้ X11 แล้ว restart เท่านั้นเอง !!

**ให้ใช้ sudo ด้วยเพราะว่าถ้าไม่เป็น root จะแก้ไขไฟล์ในส่วนนี้ไม่ได้!**

`sudo vim /etc/gdm3/daemon.conf`

เอา ( # ) ออกจาก #WaylandEnable=false → WaylandEnable=false

## เรียบร้อย!
---

##  reference
My blog on medium [link](https://piravit-chenpittaya.medium.com/%E0%B9%81%E0%B8%81%E0%B9%89-plank-error-only-x11-environments-are-supported-linux-99b075db7758)
