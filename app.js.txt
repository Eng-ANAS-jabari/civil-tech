import { initializeApp } from "firebase/app";
import { getFirestore, collection, addDoc } from "firebase/firestore";

// إعدادات مشروعك (تأكد من مطابقتها لبياناتك في Firebase)
const firebaseConfig = {
  apiKey: "AIzaSy...", 
  projectId: "civiltech-e0a16",
  authDomain: "civil-tech-web.firebaseapp.com",
  storageBucket: "civiltech-e0a16.firebasestorage.app",
  appId: "1:..." 
};

const app = initializeApp(firebaseConfig);
const db = getFirestore(app);

async function sendData() {
  try {
    const docRef = await addDoc(collection(db, "projects"), {
      projectName: "Civil Tech Management",
      developer: "TALA",
      status: "Active",
      timestamp: new Date()
    });
    console.log("✅ تمت إضافة المشروع بنجاح! رقم المستند: ", docRef.id);
  } catch (e) {
    console.error("❌ فشل في إرسال البيانات: ", e);
  }
}

sendData();