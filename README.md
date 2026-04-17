# Furkyyimport { useState, useRef } from "react";
import { motion } from "framer-motion";

export default function LovePage() {
  const [started, setStarted] = useState(false);
  const [noPos, setNoPos] = useState({ x: 50, y: 50 });
  const audioRef = useRef(null);

  const moveButton = () => {
    const x = Math.random() * window.innerWidth * 0.8;
    const y = Math.random() * window.innerHeight * 0.8;
    setNoPos({ x, y });
  };

  const startExperience = () => {
    setStarted(true);

    if (!audioRef.current) {
      audioRef.current = new Audio("KADINIM_AUDIO_DIRECT_MP3_URL");
      audioRef.current.loop = true;
      audioRef.current.volume = 0.7;
    }

    audioRef.current.play().catch(() => {
      // blocked by browser if not allowed
    });
  };

  if (!started) {
    return (
      <div className="w-screen h-screen flex items-center justify-center bg-gradient-to-br from-pink-200 to-red-300">
        <button
          onClick={startExperience}
          className="px-8 py-4 bg-white text-pink-600 font-bold rounded-2xl shadow-xl hover:scale-105 transition"
        >
          💖 Hikayeyi Başlat
        </button>
      </div>
    );
  }

  return (
    <div className="w-screen h-screen flex flex-col items-center justify-center text-center bg-gradient-to-br from-pink-200 to-red-300 overflow-hidden">
      <motion.div
        initial={{ opacity: 0, y: -20 }}
        animate={{ opacity: 1, y: 0 }}
        className="max-w-xl bg-white/80 backdrop-blur-md p-6 rounded-2xl shadow-xl"
      >
        <h1 className="text-2xl font-bold mb-4">💖</h1>

        <p className="text-lg leading-relaxed">
          Seninle geçirdiğim her an, hayatımın en güzel hikayesine dönüşüyor.
          Bu hikayenin her sayfasını seninle el ele, aynı heyecanla yazmaya devam etmek istiyorum.
          Benim için çok özelsin.
          Bir süredir beraberiz ve ben senin yanındayken kendimi hiç olmadığım kadar mutlu hissediyorum.
          Hayatımı seninle paylaşmak, seninle bir (biz) olmak beni çok mutlu eder.
        </p>

        <p className="mt-4 text-xl font-semibold">
          Benimle sevgili olur musun? ❤️
        </p>

        <div className="flex gap-6 mt-6 justify-center">
          <button className="px-6 py-2 bg-green-500 text-white rounded-xl shadow-lg hover:scale-105 transition">
            Evet 💕
          </button>
        </div>
      </motion.div>

      <motion.button
        onMouseEnter={moveButton}
        animate={{ x: noPos.x, y: noPos.y }}
        transition={{ type: "spring", stiffness: 200 }}
        className="absolute px-6 py-2 bg-gray-700 text-white rounded-xl shadow-lg"
      >
        Yoooook 😄
      </motion.button>
    </div>
  );
}
