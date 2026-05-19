# Game-Arab
import React, { useMemo, useState } from "react";

const lessons = [
  {
    id: 1,
    title: "Misi 1",
    theme: "Mufradat Madrasah",
    subtitle: "Kenali kosakata Arab yang sering muncul di sekolah.",
    badge: "Badge Penjelajah Madrasah",
    tag: "Kosakata",
    color: "from-orange-200 via-yellow-100 to-pink-100",
    sticker: "📚",
    questions: [
      {
        mode: "choice",
        prompt: "Apa arti kata berikut?",
        arabic: "الْمَدْرَسَةُ",
        answer: "Sekolah",
        options: ["Sekolah", "Masjid", "Pasar", "Rumah"],
        hint: "Tempat kamu belajar setiap hari."
      },
      {
        mode: "choice",
        prompt: "Apa arti kata berikut?",
        arabic: "الْفَصْلُ",
        answer: "Kelas",
        options: ["Kelas", "Perpustakaan", "Buku", "Guru"],
        hint: "Ruangan untuk belajar bersama teman."
      },
      {
        mode: "choice",
        prompt: "Apa arti kata berikut?",
        arabic: "الْمُعَلِّمُ",
        answer: "Guru laki-laki",
        options: ["Guru laki-laki", "Siswa", "Teman", "Penjaga sekolah"],
        hint: "Orang yang mengajar di kelas."
      },
      {
        mode: "choice",
        prompt: "Apa arti kata berikut?",
        arabic: "الْكِتَابُ",
        answer: "Buku",
        options: ["Buku", "Pulpen", "Tas", "Meja"],
        hint: "Benda yang kamu baca."
      }
    ]
  },
  {
    id: 2,
    title: "Misi 2",
    theme: "Benda Sekitar Siswa",
    subtitle: "Pilih arti kosakata sebelum energi belajar habis.",
    badge: "Badge Ahli Mufradat",
    tag: "Latihan Cepat",
    color: "from-cyan-200 via-blue-100 to-indigo-100",
    sticker: "✏️",
    questions: [
      {
        mode: "choice",
        prompt: "Apa arti kata berikut?",
        arabic: "الْقَلَمُ",
        answer: "Pulpen",
        options: ["Pulpen", "Papan tulis", "Kursi", "Jendela"],
        hint: "Alat untuk menulis."
      },
      {
        mode: "choice",
        prompt: "Apa arti kata berikut?",
        arabic: "الْحَقِيبَةُ",
        answer: "Tas",
        options: ["Tas", "Buku", "Pintu", "Kantin"],
        hint: "Tempat membawa buku."
      },
      {
        mode: "choice",
        prompt: "Apa arti kata berikut?",
        arabic: "السَّبُّورَةُ",
        answer: "Papan tulis",
        options: ["Papan tulis", "Meja", "Kursi", "Jalan"],
        hint: "Guru sering menulis di benda ini."
      },
      {
        mode: "choice",
        prompt: "Apa arti kata berikut?",
        arabic: "الْمَكْتَبَةُ",
        answer: "Perpustakaan",
        options: ["Perpustakaan", "Lapangan", "Kantin", "Masjid"],
        hint: "Tempat menyimpan dan membaca buku."
      }
    ]
  },
  {
    id: 3,
    title: "Misi 3",
    theme: "Susun Kalimat",
    subtitle: "Latih pola kalimat sederhana dengan cara menyeret ide jawaban.",
    badge: "Badge Penyusun Kalimat",
    tag: "Tarkib",
    color: "from-lime-200 via-emerald-100 to-teal-100",
    sticker: "🧩",
    questions: [
      {
        mode: "sentence",
        prompt: "Susun arti kalimat berikut.",
        arabic: "هٰذَا كِتَابٌ",
        answer: "Ini adalah buku",
        options: ["Ini", "adalah", "buku", "sekolah"],
        hint: "هٰذَا berarti ini."
      },
      {
        mode: "sentence",
        prompt: "Susun arti kalimat berikut.",
        arabic: "تِلْكَ حَقِيبَةٌ",
        answer: "Itu adalah tas",
        options: ["Itu", "adalah", "tas", "guru"],
        hint: "تِلْكَ dipakai untuk menunjuk benda muannats."
      },
      {
        mode: "sentence",
        prompt: "Susun arti kalimat berikut.",
        arabic: "الْمَدْرَسَةُ كَبِيرَةٌ",
        answer: "Sekolah itu besar",
        options: ["Sekolah", "itu", "besar", "kecil"],
        hint: "كَبِيرَةٌ berarti besar."
      }
    ]
  },
  {
    id: 4,
    title: "Misi 4",
    theme: "Hiwar Mini",
    subtitle: "Pilih respons percakapan yang paling sesuai.",
    badge: "Badge Jago Hiwar",
    tag: "Percakapan",
    color: "from-fuchsia-200 via-pink-100 to-rose-100",
    sticker: "💬",
    questions: [
      {
        mode: "choice",
        prompt: "Pilih jawaban yang tepat untuk salam berikut.",
        arabic: "السَّلَامُ عَلَيْكُمْ",
        answer: "وَعَلَيْكُمُ السَّلَامُ",
        options: ["وَعَلَيْكُمُ السَّلَامُ", "صَبَاحُ الْخَيْرِ", "أَنَا طَالِبٌ", "شُكْرًا"],
        hint: "Balasan salam dimulai dengan وَعَلَيْكُم."
      },
      {
        mode: "choice",
        prompt: "Pertanyaan ini berarti 'Siapa namamu?'. Pilih jawaban yang tepat.",
        arabic: "مَا اسْمُكَ؟",
        answer: "اسْمِي أَحْمَدُ",
        options: ["اسْمِي أَحْمَدُ", "أَنَا مِنْ إِنْدُونِيسِيَا", "هٰذَا قَلَمٌ", "فِي الْفَصْلِ"],
        hint: "Jawaban nama biasanya memakai اسْمِي."
      },
      {
        mode: "choice",
        prompt: "Pilih jawaban untuk ucapan terima kasih.",
        arabic: "شُكْرًا",
        answer: "عَفْوًا",
        options: ["عَفْوًا", "مَرْحَبًا", "أَيْنَ؟", "نَعَمْ"],
        hint: "عَفْوًا berarti sama-sama."
      }
    ]
  }
];

const allCards = [
  { arabic: "كِتَابٌ", meaning: "Buku" },
  { arabic: "قَلَمٌ", meaning: "Pulpen" },
  { arabic: "حَقِيبَةٌ", meaning: "Tas" },
  { arabic: "مُعَلِّمٌ", meaning: "Guru" },
  { arabic: "فَصْلٌ", meaning: "Kelas" },
  { arabic: "مَكْتَبَةٌ", meaning: "Perpustakaan" }
];

function shuffle(list) {
  return [...list].sort(() => Math.random() - 0.5);
}

function DoodleMascot({ mood = "happy" }) {
  const mouth = mood === "sad" ? "M24 62 Q40 51 56 62" : "M24 54 Q40 70 56 54";
  return (
    <div className="relative mx-auto h-44 w-44 select-none">
      <div className="absolute left-6 top-8 h-32 w-32 rotate-3 rounded-[2.2rem] bg-white shadow-[8px_8px_0_rgba(15,23,42,0.18)] border-4 border-slate-900" />
      <div className="absolute left-10 top-2 h-12 w-24 -rotate-6 rounded-full bg-violet-500 border-4 border-slate-900 shadow-[4px_4px_0_rgba(15,23,42,0.2)]" />
      <div className="absolute left-1 top-18 h-12 w-12 -rotate-12 rounded-full bg-yellow-300 border-4 border-slate-900" />
      <div className="absolute right-1 top-18 h-12 w-12 rotate-12 rounded-full bg-yellow-300 border-4 border-slate-900" />
      <svg className="absolute left-10 top-15" width="96" height="96" viewBox="0 0 80 80">
        <circle cx="28" cy="32" r="6" fill="#0f172a" />
        <circle cx="54" cy="32" r="6" fill="#0f172a" />
        <circle cx="30" cy="30" r="2" fill="white" />
        <circle cx="56" cy="30" r="2" fill="white" />
        <path d={mouth} stroke="#0f172a" strokeWidth="5" fill="none" strokeLinecap="round" />
      </svg>
      <div className="absolute -bottom-1 left-12 h-16 w-22 -rotate-2 rounded-3xl bg-cyan-400 border-4 border-slate-900 shadow-[5px_5px_0_rgba(15,23,42,0.18)]" />
      <div className="absolute bottom-6 left-17 text-3xl">ع</div>
      <div className="absolute right-0 top-3 rotate-12 rounded-2xl bg-yellow-300 px-3 py-2 text-sm font-black text-slate-900 border-3 border-slate-900 shadow-[3px_3px_0_rgba(15,23,42,0.25)]">Rafi</div>
      <div className="absolute left-0 bottom-8 -rotate-12 rounded-full bg-pink-400 px-3 py-1 text-sm font-black text-white border-3 border-slate-900">يلا!</div>
    </div>
  );
}

function LuluMascot() {
  return (
    <div className="relative h-28 w-28 select-none">
      <div className="absolute left-3 top-5 h-20 w-20 rounded-[2rem] bg-white border-4 border-slate-900 shadow-[5px_5px_0_rgba(15,23,42,0.22)]" />
      <div className="absolute left-4 top-1 h-9 w-9 -rotate-12 rounded-t-full bg-white border-4 border-slate-900" />
      <div className="absolute right-5 top-1 h-9 w-9 rotate-12 rounded-t-full bg-white border-4 border-slate-900" />
      <div className="absolute left-9 top-13 h-2.5 w-2.5 rounded-full bg-slate-900" />
      <div className="absolute right-10 top-13 h-2.5 w-2.5 rounded-full bg-slate-900" />
      <div className="absolute left-13 top-17 h-2 w-4 rounded-full bg-pink-400" />
      <div className="absolute bottom-0 left-5 -rotate-6 rounded-xl bg-violet-500 px-3 py-1 text-xs font-black text-white border-2 border-slate-900">Lulu</div>
    </div>
  );
}

function Tape({ className = "" }) {
  return <div className={`absolute h-7 w-20 rotate-[-8deg] rounded-sm bg-yellow-200/80 border border-yellow-300 ${className}`} />;
}

function StudentBadge({ children }) {
  return (
    <span className="inline-flex items-center rounded-full bg-white px-3 py-1 text-xs font-black text-slate-800 border-2 border-slate-900 shadow-[3px_3px_0_rgba(15,23,42,0.15)]">
      {children}
    </span>
  );
}

function ProgressBar({ value }) {
  return (
    <div className="h-4 w-full overflow-hidden rounded-full bg-white border-2 border-slate-900 shadow-[3px_3px_0_rgba(15,23,42,0.2)]">
      <div
        className="h-full rounded-r-full bg-gradient-to-r from-violet-500 via-pink-500 to-orange-400 transition-all duration-500"
        style={{ width: `${Math.max(0, Math.min(100, value))}%` }}
      />
    </div>
  );
}

function AppButton({ children, onClick, disabled, className = "", variant = "primary" }) {
  const base = "rounded-2xl px-4 py-3 font-black transition active:translate-x-1 active:translate-y-1 disabled:opacity-50 disabled:cursor-not-allowed";
  const styles = variant === "primary"
    ? "bg-slate-900 text-white border-2 border-slate-900 shadow-[5px_5px_0_rgba(109,40,217,0.55)] hover:bg-violet-700"
    : variant === "soft"
    ? "bg-white text-slate-900 border-2 border-slate-900 shadow-[4px_4px_0_rgba(15,23,42,0.16)] hover:bg-yellow-50"
    : "bg-yellow-300 text-slate-900 border-2 border-slate-900 shadow-[5px_5px_0_rgba(15,23,42,0.22)] hover:bg-yellow-400";
  return <button onClick={onClick} disabled={disabled} className={`${base} ${styles} ${className}`}>{children}</button>;
}

function Home({ startLesson, openMatch }) {
  return (
    <div className="min-h-screen bg-[#fff7e6] text-slate-900 overflow-hidden">
      <div className="fixed inset-0 opacity-45 pointer-events-none" style={{ backgroundImage: "radial-gradient(#111827 1px, transparent 1px)", backgroundSize: "24px 24px" }} />
      <div className="relative mx-auto max-w-7xl p-4 md:p-8">
        <div className="mb-5 flex flex-wrap items-center justify-between gap-3">
          <div className="flex items-center gap-3">
            <div className="flex h-14 w-14 rotate-[-4deg] items-center justify-center rounded-2xl bg-violet-500 text-3xl border-4 border-slate-900 shadow-[5px_5px_0_rgba(15,23,42,0.22)]">ع</div>
            <div>
              <div className="text-xs font-black uppercase tracking-[0.28em] text-violet-700">Prototype Mahasiswa</div>
              <h2 className="text-xl font-black">Arabiyah Quest MTs</h2>
            </div>
          </div>
          <StudentBadge>Versi Demo Interaktif</StudentBadge>
        </div>

        <div className="grid gap-6 lg:grid-cols-[1.15fr_0.85fr] items-stretch">
          <div className="relative rounded-[2rem] bg-white p-6 md:p-8 border-4 border-slate-900 shadow-[12px_12px_0_rgba(15,23,42,0.2)]">
            <Tape className="left-12 -top-3" />
            <Tape className="right-16 -bottom-3 rotate-6" />
            <div className="flex flex-wrap gap-2">
              <StudentBadge>Game Edukasi</StudentBadge>
              <StudentBadge>Bahasa Arab</StudentBadge>
              <StudentBadge>MTs Kelas VII sampai IX</StudentBadge>
            </div>
            <h1 className="mt-5 max-w-3xl text-4xl md:text-6xl font-black leading-[1.02] tracking-tight">
              Belajar Bahasa Arab lewat misi, skor, dan kartun seru.
            </h1>
            <p className="mt-5 max-w-2xl text-base md:text-lg leading-relaxed text-slate-700">
              Media ini dirancang seperti proyek kreatif mahasiswa. Siswa belajar *mufradat*, *tarkib*, dan *hiwar* melalui tantangan singkat, visual kartun, kartu pasangan, serta umpan balik langsung.
            </p>
            <div className="mt-7 grid gap-3 sm:grid-cols-3">
              <div className="rotate-[-1deg] rounded-3xl bg-pink-100 p-4 border-3 border-slate-900 shadow-[5px_5px_0_rgba(15,23,42,0.18)]">
                <div className="text-3xl">🎮</div>
                <div className="mt-2 font-black">Kuis Misi</div>
                <div className="text-sm text-slate-600">Jawab soal Arab dengan cepat.</div>
              </div>
              <div className="rotate-[1deg] rounded-3xl bg-cyan-100 p-4 border-3 border-slate-900 shadow-[5px_5px_0_rgba(15,23,42,0.18)]">
                <div className="text-3xl">🧠</div>
                <div className="mt-2 font-black">Latihan Ingatan</div>
                <div className="text-sm text-slate-600">Cocokkan kata dan arti.</div>
              </div>
              <div className="rotate-[-1deg] rounded-3xl bg-lime-100 p-4 border-3 border-slate-900 shadow-[5px_5px_0_rgba(15,23,42,0.18)]">
                <div className="text-3xl">🏅</div>
                <div className="mt-2 font-black">Badge Belajar</div>
                <div className="text-sm text-slate-600">Dapatkan lencana tiap misi.</div>
              </div>
            </div>
          </div>

          <div className="relative min-h-[430px] rounded-[2rem] bg-gradient-to-br from-violet-500 via-fuchsia-400 to-orange-300 p-6 border-4 border-slate-900 shadow-[12px_12px_0_rgba(15,23,42,0.22)] overflow-hidden">
            <div className="absolute left-5 top-5 rounded-full bg-white/25 px-4 py-2 text-sm font-black text-white border-2 border-white/40">Kartun Edukatif</div>
            <div className="absolute -right-14 -top-14 h-44 w-44 rounded-full bg-white/20" />
            <div className="absolute -left-14 -bottom-14 h-52 w-52 rounded-full bg-yellow-200/50" />
            <div className="relative pt-12">
              <DoodleMascot />
              <div className="mx-auto mt-5 max-w-sm -rotate-1 rounded-3xl bg-white p-5 text-center text-slate-900 border-4 border-slate-900 shadow-[8px_8px_0_rgba(15,23,42,0.22)]">
                <div className="text-sm font-black uppercase tracking-widest text-violet-600">Pesan Rafi</div>
                <h2 className="mt-1 text-2xl font-black">Ayo selesaikan misi Arabiyah!</h2>
                <p className="mt-2 text-sm text-slate-600">Belajar dibuat ringan, visual, dan penuh tantangan agar siswa tidak cepat bosan.</p>
              </div>
            </div>
          </div>
        </div>

        <div className="mt-7 grid gap-5 md:grid-cols-4">
          {lessons.map((lesson, idx) => (
            <div key={lesson.id} className={`relative rounded-[1.75rem] bg-gradient-to-br ${lesson.color} p-5 border-4 border-slate-900 shadow-[8px_8px_0_rgba(15,23,42,0.18)] ${idx % 2 ? "rotate-[0.7deg]" : "rotate-[-0.7deg]"}`}>
              <Tape className="left-8 -top-3 scale-75" />
              <div className="flex items-start justify-between gap-3">
                <div>
                  <div className="text-xs font-black uppercase tracking-widest text-slate-600">{lesson.title}</div>
                  <h3 className="mt-1 text-xl font-black leading-tight">{lesson.theme}</h3>
                </div>
                <div className="flex h-13 w-13 items-center justify-center rounded-2xl bg-white text-3xl border-3 border-slate-900 shadow-[3px_3px_0_rgba(15,23,42,0.2)]">{lesson.sticker}</div>
              </div>
              <div className="mt-3 inline-flex rounded-full bg-white/80 px-3 py-1 text-xs font-black border-2 border-slate-900">{lesson.tag}</div>
              <p className="mt-3 min-h-16 text-sm leading-relaxed text-slate-700">{lesson.subtitle}</p>
              <AppButton onClick={() => startLesson(lesson.id)} className="mt-4 w-full">Mulai Misi</AppButton>
            </div>
          ))}
        </div>

        <div className="mt-7 relative rounded-[1.75rem] bg-slate-900 p-5 md:p-6 text-white border-4 border-slate-900 shadow-[10px_10px_0_rgba(124,58,237,0.35)] overflow-hidden">
          <div className="absolute right-0 top-0 h-36 w-36 rounded-bl-full bg-violet-500/50" />
          <div className="relative flex flex-col gap-5 md:flex-row md:items-center md:justify-between">
            <div className="flex items-center gap-4">
              <LuluMascot />
              <div>
                <div className="text-sm font-black uppercase tracking-widest text-yellow-300">Mini Game Bonus</div>
                <h3 className="text-2xl font-black">Kartu Pasangan Mufradat</h3>
                <p className="mt-1 max-w-2xl text-white/75">Siswa mencocokkan kartu Arab dengan arti bahasa Indonesia. Cocok untuk pemanasan, apersepsi, atau evaluasi ringan.</p>
              </div>
            </div>
            <AppButton onClick={openMatch} variant="accent" className="md:w-60">Mainkan Bonus</AppButton>
          </div>
        </div>
      </div>
    </div>
  );
}

function LessonScreen({ lesson, goHome, finishLesson }) {
  const [index, setIndex] = useState(0);
  const [score, setScore] = useState(0);
  const [lives, setLives] = useState(3);
  const [feedback, setFeedback] = useState(null);
  const [selectedWords, setSelectedWords] = useState([]);
  const [showHint, setShowHint] = useState(false);

  const q = lesson.questions[index];
  const progress = (index / lesson.questions.length) * 100;
  const mood = feedback === "wrong" ? "sad" : "happy";

  function nextQuestion(extraScore = 0, wrong = false) {
    const newScore = score + extraScore;
    const newLives = wrong ? lives - 1 : lives;
    setScore(newScore);
    setLives(newLives);
    setFeedback(null);
    setSelectedWords([]);
    setShowHint(false);

    if (newLives <= 0) {
      finishLesson({ score: newScore, max: lesson.questions.length * 10, badge: null, failed: true });
      return;
    }

    if (index + 1 >= lesson.questions.length) {
      finishLesson({ score: newScore, max: lesson.questions.length * 10, badge: lesson.badge, failed: false });
      return;
    }

    setIndex(index + 1);
  }

  function answerChoice(option) {
    const correct = option === q.answer;
    setFeedback(correct ? "correct" : "wrong");
    setTimeout(() => nextQuestion(correct ? 10 : 0, !correct), 750);
  }

  function tapWord(word) {
    if (selectedWords.includes(word)) return;
    setSelectedWords([...selectedWords, word]);
  }

  function removeWord(wordIndex) {
    setSelectedWords(selectedWords.filter((_, i) => i !== wordIndex));
  }

  function checkSentence() {
    const sentence = selectedWords.join(" ");
    const correct = sentence === q.answer;
    setFeedback(correct ? "correct" : "wrong");
    setTimeout(() => nextQuestion(correct ? 10 : 0, !correct), 850);
  }

  return (
    <div className={`min-h-screen bg-gradient-to-br ${lesson.color} p-4 md:p-8 text-slate-900`}>
      <div className="fixed inset-0 opacity-30 pointer-events-none" style={{ backgroundImage: "linear-gradient(#111827 1px, transparent 1px), linear-gradient(90deg, #111827 1px, transparent 1px)", backgroundSize: "36px 36px" }} />
      <div className="relative mx-auto max-w-6xl">
        <div className="mb-5 rounded-[1.75rem] bg-white p-4 border-4 border-slate-900 shadow-[7px_7px_0_rgba(15,23,42,0.18)]">
          <div className="flex flex-col gap-4 md:flex-row md:items-center md:justify-between">
            <div>
              <button onClick={goHome} className="text-sm font-black text-violet-700 hover:underline">← Kembali ke beranda</button>
              <h1 className="mt-1 text-2xl md:text-4xl font-black">{lesson.title}: {lesson.theme}</h1>
            </div>
            <div className="flex flex-wrap gap-2">
              <div className="rounded-2xl bg-yellow-200 px-4 py-2 border-3 border-slate-900 font-black shadow-[3px_3px_0_rgba(15,23,42,0.18)]">Skor {score}</div>
              <div className="rounded-2xl bg-pink-200 px-4 py-2 border-3 border-slate-900 font-black shadow-[3px_3px_0_rgba(15,23,42,0.18)]">Energi {"⚡".repeat(Math.max(0, lives))}</div>
            </div>
          </div>
          <div className="mt-4">
            <ProgressBar value={progress} />
          </div>
        </div>

        <div className="grid gap-5 md:grid-cols-[0.8fr_1.2fr]">
          <div className="relative rounded-[2rem] bg-white p-5 border-4 border-slate-900 shadow-[9px_9px_0_rgba(15,23,42,0.2)] text-center">
            <Tape className="left-10 -top-3" />
            <DoodleMascot mood={mood} />
            <h2 className="mt-2 text-2xl font-black">Rafi memberi tantangan</h2>
            <p className="mt-2 text-slate-600 leading-relaxed">Pilih jawaban dengan teliti. Gunakan petunjuk jika kamu mulai ragu.</p>
            <AppButton onClick={() => setShowHint(!showHint)} variant="soft" className="mt-4 w-full">{showHint ? "Tutup Petunjuk" : "Lihat Petunjuk"}</AppButton>
            {showHint && <div className="mt-4 -rotate-1 rounded-2xl bg-yellow-100 p-4 text-sm font-semibold text-slate-800 border-3 border-slate-900 shadow-[4px_4px_0_rgba(15,23,42,0.16)]">💡 {q.hint}</div>}
          </div>

          <div className="relative rounded-[2rem] bg-white p-5 md:p-7 border-4 border-slate-900 shadow-[9px_9px_0_rgba(15,23,42,0.2)]">
            <Tape className="right-12 -top-3 rotate-6" />
            <div className="flex flex-wrap items-center justify-between gap-3">
              <StudentBadge>Soal {index + 1} dari {lesson.questions.length}</StudentBadge>
              <StudentBadge>{lesson.tag}</StudentBadge>
            </div>
            <h2 className="mt-4 text-xl md:text-2xl font-black">{q.prompt}</h2>
            <div dir="rtl" className="mt-5 rounded-[1.5rem] bg-slate-900 px-5 py-7 text-center text-4xl md:text-6xl font-black text-white border-4 border-slate-900 shadow-inner leading-relaxed">
              {q.arabic}
            </div>

            {feedback && (
              <div className={`mt-4 rounded-2xl p-4 text-center font-black border-3 border-slate-900 shadow-[4px_4px_0_rgba(15,23,42,0.16)] ${feedback === "correct" ? "bg-lime-200 text-slate-900" : "bg-rose-200 text-slate-900"}`}>
                {feedback === "correct" ? "Benar. Skor bertambah 10." : "Belum tepat. Coba perhatikan petunjuknya."}
              </div>
            )}

            {q.mode === "choice" && (
              <div className="mt-5 grid gap-3 sm:grid-cols-2">
                {q.options.map((option, optionIndex) => (
                  <AppButton key={option} onClick={() => answerChoice(option)} variant="soft" disabled={!!feedback} className={`${optionIndex % 2 ? "rotate-[0.5deg]" : "rotate-[-0.5deg]"} text-left min-h-16`}>
                    {option}
                  </AppButton>
                ))}
              </div>
            )}

            {q.mode === "sentence" && (
              <div className="mt-5">
                <div className="min-h-24 rounded-2xl border-4 border-dashed border-violet-400 bg-violet-50 p-3 flex flex-wrap gap-2 items-center">
                  {selectedWords.length === 0 && <span className="font-semibold text-slate-400">Ketuk kata di bawah untuk menyusun jawaban.</span>}
                  {selectedWords.map((word, i) => (
                    <button key={`${word}-${i}`} onClick={() => removeWord(i)} className="rounded-xl bg-white px-3 py-2 font-black border-2 border-slate-900 shadow-[3px_3px_0_rgba(15,23,42,0.16)]">{word}</button>
                  ))}
                </div>
                <div className="mt-4 grid gap-3 sm:grid-cols-4">
                  {q.options.map((word) => (
                    <AppButton key={word} onClick={() => tapWord(word)} variant="soft" disabled={selectedWords.includes(word) || !!feedback}>{word}</AppButton>
                  ))}
                </div>
                <div className="mt-4 flex gap-3">
                  <AppButton onClick={checkSentence} disabled={selectedWords.length < 3 || !!feedback} className="flex-1">Periksa Jawaban</AppButton>
                  <AppButton onClick={() => setSelectedWords([])} variant="soft" disabled={!!feedback}>Reset</AppButton>
                </div>
              </div>
            )}
          </div>
        </div>
      </div>
    </div>
  );
}

function ResultScreen({ result, goHome, replay }) {
  const percent = Math.round((result.score / result.max) * 100);
  return (
    <div className="min-h-screen bg-[#fff7e6] p-4 md:p-8 flex items-center justify-center text-slate-900">
      <div className="fixed inset-0 opacity-35 pointer-events-none" style={{ backgroundImage: "radial-gradient(#111827 1px, transparent 1px)", backgroundSize: "24px 24px" }} />
      <div className="relative max-w-xl w-full rounded-[2rem] bg-white p-7 border-4 border-slate-900 shadow-[12px_12px_0_rgba(15,23,42,0.22)] text-center">
        <Tape className="left-14 -top-3" />
        <DoodleMascot mood={result.failed ? "sad" : "happy"} />
        <h1 className="mt-4 text-4xl font-black">{result.failed ? "Misi Belum Selesai" : "Misi Berhasil"}</h1>
        <p className="mt-2 text-slate-600">Skor kamu {result.score} dari {result.max}. Nilai latihan {percent}.</p>
        <div className="mt-5 rounded-[1.5rem] bg-yellow-100 p-5 border-4 border-slate-900 shadow-[6px_6px_0_rgba(15,23,42,0.18)]">
          <div className="text-5xl">{result.failed ? "💪" : "🏆"}</div>
          <div className="mt-2 text-xl font-black">{result.failed ? "Ulangi misi untuk menguatkan hafalan." : result.badge}</div>
          <div className="mt-1 text-sm text-slate-600">Belajar bahasa Arab jadi lebih mudah jika kamu berlatih sedikit demi sedikit.</div>
        </div>
        <div className="mt-6 grid gap-3 sm:grid-cols-2">
          <AppButton onClick={replay}>Main Lagi</AppButton>
          <AppButton onClick={goHome} variant="soft">Beranda</AppButton>
        </div>
      </div>
    </div>
  );
}

function MatchGame({ goHome }) {
  const initialDeck = useMemo(() => {
    const selected = allCards.slice(0, 5);
    const deck = selected.flatMap((item, idx) => [
      { id: `a-${idx}`, pair: idx, type: "arabic", text: item.arabic },
      { id: `m-${idx}`, pair: idx, type: "meaning", text: item.meaning }
    ]);
    return shuffle(deck);
  }, []);

  const [deck, setDeck] = useState(initialDeck);
  const [open, setOpen] = useState([]);
  const [matched, setMatched] = useState([]);
  const [moves, setMoves] = useState(0);

  function resetGame() {
    const selected = allCards.slice(0, 5);
    const newDeck = shuffle(selected.flatMap((item, idx) => [
      { id: `a-${idx}-${Date.now()}`, pair: idx, type: "arabic", text: item.arabic },
      { id: `m-${idx}-${Date.now()}`, pair: idx, type: "meaning", text: item.meaning }
    ]));
    setDeck(newDeck);
    setOpen([]);
    setMatched([]);
    setMoves(0);
  }

  function tapCard(card) {
    if (matched.includes(card.pair) || open.some((c) => c.id === card.id) || open.length >= 2) return;
    const next = [...open, card];
    setOpen(next);
    if (next.length === 2) {
      setMoves(moves + 1);
      const isPair = next[0].pair === next[1].pair && next[0].type !== next[1].type;
      setTimeout(() => {
        if (isPair) setMatched([...matched, next[0].pair]);
        setOpen([]);
      }, 650);
    }
  }

  const finished = matched.length === 5;

  return (
    <div className="min-h-screen bg-slate-950 p-4 md:p-8 text-white overflow-hidden">
      <div className="fixed inset-0 opacity-20 pointer-events-none" style={{ backgroundImage: "radial-gradient(#facc15 1.5px, transparent 1.5px)", backgroundSize: "26px 26px" }} />
      <div className="relative mx-auto max-w-6xl">
        <div className="mb-5 rounded-[1.75rem] bg-white text-slate-900 p-4 border-4 border-slate-900 shadow-[8px_8px_0_rgba(250,204,21,0.5)]">
          <div className="flex flex-col gap-3 md:flex-row md:items-center md:justify-between">
            <div>
              <button onClick={goHome} className="text-sm font-black text-violet-700 hover:underline">← Kembali ke beranda</button>
              <h1 className="mt-1 text-3xl font-black">Kartu Pasangan Mufradat</h1>
              <p className="text-slate-600">Cocokkan kartu Arab dengan arti yang benar.</p>
            </div>
            <div className="rounded-2xl bg-yellow-200 px-4 py-2 font-black border-3 border-slate-900 shadow-[3px_3px_0_rgba(15,23,42,0.18)]">Gerakan {moves}</div>
          </div>
        </div>

        <div className="grid gap-5 md:grid-cols-[0.7fr_1.3fr]">
          <div className="relative rounded-[2rem] bg-violet-500 p-5 border-4 border-slate-900 shadow-[10px_10px_0_rgba(250,204,21,0.45)]">
            <LuluMascot />
            <h2 className="mt-4 text-2xl font-black">Pesan Lulu</h2>
            <p className="mt-2 text-white/85 leading-relaxed">Buka dua kartu. Jika kosakata dan artinya cocok, kartu akan terkunci. Selesaikan semua pasangan untuk menang.</p>
            {finished && (
              <div className="mt-4 rounded-2xl bg-lime-200 p-4 text-slate-900 font-black border-3 border-slate-900 shadow-[4px_4px_0_rgba(15,23,42,0.18)]">
                Hebat. Kamu menemukan semua pasangan dalam {moves} gerakan.
              </div>
            )}
            <AppButton onClick={resetGame} variant="accent" className="mt-4 w-full">Acak Ulang</AppButton>
          </div>

          <div className="grid grid-cols-2 sm:grid-cols-5 gap-3">
            {deck.map((card, idx) => {
              const isOpen = open.some((c) => c.id === card.id) || matched.includes(card.pair);
              return (
                <button
                  key={card.id}
                  onClick={() => tapCard(card)}
                  className={`min-h-30 rounded-[1.5rem] border-4 p-3 text-center font-black transition active:translate-x-1 active:translate-y-1 ${idx % 2 ? "rotate-[0.8deg]" : "rotate-[-0.8deg]"} ${isOpen ? "bg-white text-slate-900 border-slate-900 shadow-[6px_6px_0_rgba(250,204,21,0.5)]" : "bg-slate-800 text-white border-white shadow-[6px_6px_0_rgba(124,58,237,0.6)] hover:bg-slate-700"}`}
                >
                  <div className={card.type === "arabic" && isOpen ? "text-3xl" : "text-lg"} dir={card.type === "arabic" ? "rtl" : "ltr"}>{isOpen ? card.text : "؟"}</div>
                  {isOpen && <div className="mt-2 text-xs text-slate-500">{card.type === "arabic" ? "Arab" : "Arti"}</div>}
                </button>
              );
            })}
          </div>
        </div>
      </div>
    </div>
  );
}

export default function ArabicGameLearningApp() {
  const [screen, setScreen] = useState("home");
  const [activeLessonId, setActiveLessonId] = useState(null);
  const [lastResult, setLastResult] = useState(null);

  const activeLesson = lessons.find((lesson) => lesson.id === activeLessonId);

  function startLesson(id) {
    setActiveLessonId(id);
    setScreen("lesson");
  }

  function finishLesson(result) {
    setLastResult(result);
    setScreen("result");
  }

  function replay() {
    setScreen("lesson");
    setLastResult(null);
  }

  function goHome() {
    setScreen("home");
    setActiveLessonId(null);
    setLastResult(null);
  }

  if (screen === "lesson" && activeLesson) {
    return <LessonScreen key={activeLessonId + String(lastResult)} lesson={activeLesson} goHome={goHome} finishLesson={finishLesson} />;
  }

  if (screen === "result" && lastResult) {
    return <ResultScreen result={lastResult} goHome={goHome} replay={replay} />;
  }

  if (screen === "match") {
    return <MatchGame goHome={goHome} />;
  }

  return <Home startLesson={startLesson} openMatch={() => setScreen("match")} />;
}
