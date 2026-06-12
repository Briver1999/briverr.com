# ورق — Admin Panel via GitHub Actions

## كيف تستخدم لوحة الإدارة

1. افتح مستودع `Briver1999/waraq-hub` على GitHub
2. اضغط على تبويب **Actions**
3. اختر الـ workflow المطلوب من القائمة اليسرى
4. اضغط **Run workflow**
5. أدخل البيانات المطلوبة واضغط **Run**
6. شوف النتائج في الـ Summary

---

## الـ Workflows المتاحة

| الاسم | الوظيفة | يدوي / تلقائي |
|-------|---------|--------------|
| 🔍 بحث عن مستخدم | عرض بيانات مستخدم كاملة | يدوي |
| ⏳ تمديد التجربة | إضافة 3/7/14/21/30 يوم | يدوي |
| 🚫 تعطيل / تفعيل | حظر أو رفع حظر حساب | يدوي |
| 📊 تقرير الإحصائيات | عدد المستخدمين والعناصر | يدوي + كل إثنين |
| 📥 تصدير المستخدمين | CSV لكل المستخدمين أو بفلتر | يدوي |
| 📧 إرسال إشعار | للكل أو لمستخدم معين | يدوي |
| 💾 نسخ احتياطي | تصدير كل الجداول | يدوي + كل أحد |

---

## الإعداد — Secrets المطلوبة

في GitHub → Settings → Secrets → Actions أضف:

| المتغير | أين تجده |
|---------|---------|
| `SUPABASE_URL` | Supabase Dashboard → Settings → API |
| `SUPABASE_SERVICE_KEY` | Supabase Dashboard → Settings → API → service_role |

---

## خطوات النشر

```bash
# انسخ مجلد .github/workflows إلى مستودع waraq-hub
cp -r .github/workflows/* /path/to/waraq-hub/.github/workflows/
git add .
git commit -m "Add admin workflows"
git push
```
