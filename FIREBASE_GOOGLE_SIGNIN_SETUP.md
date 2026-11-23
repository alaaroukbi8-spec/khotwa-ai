# إعداد تسجيل الدخول بواسطة Google في KHOTWA AI

هذه الخطوات مطلوبة لتفعيل تسجيل الدخول الحقيقي؛ الكود موجود في الموقع لكنه يبقى معطلاً إلى أن تكتمل إعدادات Firebase.

1. افتح Firebase Console وأنشئ مشروع Firebase إذا كان مسموحاً لك بإدارة مشروع مطوّر وقبول شروط الخدمة.
2. أضف تطبيق Web إلى المشروع.
3. في Authentication > Sign-in method، فعّل Google واحفظ التغيير.
4. في Authentication > Settings > Authorized domains، أضف:
   `alaaroukbi8-spec.github.io`
5. انسخ إعدادات تطبيق الويب من Project settings > Your apps.
6. افتح `firebase-config.js` في هذا المستودع واستبدل `null` بكائن إعدادات تطبيق الويب:
   ```js
   window.KHOTWA_FIREBASE_CONFIG = {
     apiKey: "WEB_APP_API_KEY",
     authDomain: "PROJECT_ID.firebaseapp.com",
     projectId: "PROJECT_ID",
     appId: "WEB_APP_APP_ID"
   };
   ```
7. احفظ التغيير في فرع `main` وانتظر إعادة نشر GitHub Pages.

ملاحظات أمان:
- إعدادات Firebase الخاصة بتطبيق الويب عامة بطبيعتها، لكن يجب حماية البيانات بواسطة Firebase Security Rules.
- لا تضع مطلقاً service-account JSON أو private key أو كلمة مرور في ملفات الموقع.
- تسجيل الدخول يثبت هوية المستخدم فقط. مزامنة سجل المحادثات مع حساب Google عبر Firestore تحتاج إلى مخطط قاعدة بيانات وقواعد أمان إضافية، ولم تُفعّل بعد.
- إذا لم تكن مخولاً قانونياً بقبول شروط Firebase/Google Cloud، فلا تقبلها ولا تستخدم حساب شخص آخر؛ اطلب من مالك مشروع مخوّل إكمال الإعداد.
