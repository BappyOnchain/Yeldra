# 🎬 Gopal Bhar Video Auto-Cutter (Termux + ffmpeg)

প্রতিটা এপিসোডের ভিডিও থেকে প্রথম ২৫ সেকেন্ড আর শেষের ৫ সেকেন্ড
স্বয়ংক্রিয়ভাবে বাদ দিয়ে, ফাইনাল ভিডিও Bappy ফোল্ডারে সেভ করার
জন্য একটা রিইউজেবল স্ক্রিপ্ট।

---

## ✅ প্রয়োজনীয়তা

- Termux অ্যাপ (Android)
- ffmpeg ইনস্টল করা থাকতে হবে
- bc (ক্যালকুলেশনের জন্য)

pkg install ffmpeg -y
pkg install bc -y
termux-setup-storage

---

## ⚙️ ধাপ ১: একবারের জন্য স্ক্রিপ্ট সেটাপ

নিচের পুরো ব্লকটা Termux-এ কপি-পেস্ট করে Enter চাপো (এটা শুধু একবারই করতে হবে):

cat > ~/cut.sh << 'EOF'
#!/bin/bash
cd ~

INPUT="input.mp4"

echo "Detecting video duration..."
DURATION=$(ffprobe -v error -show_entries format=duration -of default=noprint_wrappers=1:nokey=1 "$INPUT")

END=$(echo "$DURATION - 5" | bc)

echo "Total duration: $DURATION sec"
echo "Cutting from 25 sec to $END sec..."

ffmpeg -y -i "$INPUT" -ss 25 -to $END -c copy final.mp4

echo "Saving to gallery (Bappy folder)..."
OUTNAME="final_$(date +%Y%m%d_%H%M%S).mp4"
cp final.mp4 ~/storage/shared/Bappy/"$OUTNAME"

echo "Cleaning up temp files..."
rm -f input.mp4 final.mp4

echo "DONE! Saved to Bappy folder as: $OUTNAME"
EOF

---

## 🎥 ধাপ ২: প্রতিটা নতুন এপিসোডে যা করবে (মাত্র ২টা কমান্ড)

কমান্ড ১ - ভিডিও ফাইল Termux-এ আনো (ফাইলের নাম বদলে দিও):

cp ~/storage/shared/Bappy/"এপিসোডের নাম.mp4" ~/input.mp4

কমান্ড ২ - কাটার স্ক্রিপ্ট চালাও:

bash ~/cut.sh

---

## 🔄 যা অটোমেটিক হবে

- ভিডিওর মোট দৈর্ঘ্য বের হবে
- প্রথম ২৫ সেকেন্ড বাদ যাবে
- শেষের ৫ সেকেন্ড বাদ যাবে
- কাটা ভিডিও Bappy ফোল্ডারে নতুন নামে (final_তারিখ_সময়.mp4) সেভ হবে
- টেম্প ফাইল অটোমেটিক মুছে যাবে

শেষে "DONE! Saved to Bappy folder as: ..." লেখা আসলেই কাজ শেষ।

---

## 🧹 এক্সট্রা: Termux-এর অপ্রয়োজনীয় ফাইল ক্লিন করার কমান্ড

যখনই Termux-এর সাইজ বেশি মনে হবে, নিচের লাইনটা রান করো
(Bappy ফোল্ডারের ভিডিও সেফ থাকবে, শুধু Termux-এর ভিতরের কাজের ফাইল মুছবে):

rm -f ~/*.mp4 ~/*.txt && apt clean -y && pkg autoclean -y && rm -rf ~/.cache/* && rm -rf $PREFIX/tmp/* && du -sh ~

চেক করো cut.sh স্ক্রিপ্ট এখনো আছে কিনা:

ls ~/cut.sh

যদি "No such file or directory" দেখায়, ধাপ ১ আবার করে স্ক্রিপ্ট বানাতে হবে।