import React, { useState } from "react";

export default function App() { const [image, setImage] = useState(null); const [info, setInfo] = useState("");

const handleImageUpload = (e) => { const file = e.target.files[0]; if (!file) return;

setImage(URL.createObjectURL(file));
setInfo(`\n📷 फ़ाइल का नाम: ${file.name}\n📦 आकार: ${(file.size / 1024).toFixed(2)} KB\n🖼️ प्रकार: ${file.type}`);

};

return ( <div className="min-h-screen bg-gray-100 flex items-center justify-center p-4"> <div className="bg-white rounded-2xl shadow-lg p-6 w-full max-w-md"> <h1 className="text-2xl font-bold mb-4 text-center">📤 इमेज अपलोड प्लेटफ़ॉर्म</h1>

<input
      type="file"
      accept="image/*"
      onChange={handleImageUpload}
      className="w-full mb-4"
    />

    {image && (
      <div className="mb-4">
        <p className="font-semibold mb-2">अपलोड की गई इमेज:</p>
        <img
          src={image}
          alt="Preview"
          className="rounded-xl w-full object-cover"
        />
      </div>
    )}

    {info && (
      <pre className="bg-gray-50 p-3 rounded-lg text-sm whitespace-pre-wrap">
        {info}
      </pre>
    )}

    <p className="text-xs text-center text-gray-500 mt-4">
      यह ऐप इमेज अपलोड करते समय तुरंत जानकारी हिंदी में दिखाता है
    </p>
  </div>
</div>

); }