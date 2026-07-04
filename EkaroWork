import React, { useState, useEffect, useMemo } from "react";
import {
  Home, Compass, Briefcase, Wrench, Sparkles, MapPin, Copy, Check,
  ChevronDown, ChevronRight, ExternalLink, Search, Loader2, RefreshCw,
  FileText, CreditCard, BookOpen, Wand2, ArrowRight, Shield, AlertTriangle, Lock
} from "lucide-react";

// ---------- Design tokens ----------
const C = {
  forest: "#0B3D2E",
  forestDark: "#082C21",
  gold: "#F2B705",
  paper: "#FBF6EC",
  card: "#FFFFFF",
  ink: "#201D1A",
  inkSoft: "#5B564E",
  terracotta: "#C64B3C",
  greenTint: "#E4EFE6",
  line: "#E7E0D2",
};
const displayFont = "'Sora', system-ui, sans-serif";
const bodyFont = "'Inter', system-ui, sans-serif";
const monoFont = "'JetBrains Mono', monospace";

const FONT_IMPORT = "@import url('https://fonts.googleapis.com/css2?family=Sora:wght@400;600;700;800&family=Inter:wght@400;500;600;700&family=JetBrains+Mono:wght@500&display=swap');";

// ---------- Copy button ----------
function CopyBtn({ text, small }) {
  const [done, setDone] = useState(false);
  return (
    <button
      onClick={() => {
        navigator.clipboard.writeText(text).then(() => {
          setDone(true);
          setTimeout(() => setDone(false), 1500);
        });
      }}
      style={{
        display: "inline-flex", alignItems: "center", gap: 6,
        background: done ? C.forest : C.greenTint,
        color: done ? "#fff" : C.forest,
        border: "none", borderRadius: 8,
        padding: small ? "6px 10px" : "8px 14px",
        fontSize: small ? 12 : 13, fontWeight: 600, cursor: "pointer",
        fontFamily: bodyFont, transition: "all .15s",
      }}
    >
      {done ? <Check size={14} /> : <Copy size={14} />}
      {done ? "Copied" : "Copy"}
    </button>
  );
}

// ---------- Section heading ----------
function SectionTitle({ eyebrow, title, sub }) {
  return (
    <div style={{ marginBottom: 18 }}>
      {eyebrow && (
        <div style={{ fontFamily: monoFont, fontSize: 11, letterSpacing: 1.5, color: C.terracotta, textTransform: "uppercase", marginBottom: 6 }}>
          {eyebrow}
        </div>
      )}
      <h2 style={{ fontFamily: displayFont, fontWeight: 800, fontSize: 22, color: C.ink, margin: 0 }}>{title}</h2>
      {sub && <p style={{ fontFamily: bodyFont, color: C.inkSoft, fontSize: 14, marginTop: 6, lineHeight: 1.5 }}>{sub}</p>}
    </div>
  );
}

// ============================================================
// HOME — the Trail map
// ============================================================
function HomeTab({ goTo, result }) {
  const stops = [
    { id: "match", label: "Find your path", desc: "Take the 2-minute quiz to see which remote path fits you.", icon: Compass },
    { id: "jobs", label: "See live remote jobs", desc: "Real openings, updated from the web, filtered for you.", icon: Briefcase },
    { id: "toolkit", label: "Build your CV, get paid & stay safe", desc: "Make a job-ready CV, learn how to get paid from abroad, and spot scams before they cost you.", icon: Wrench },
    { id: "grow", label: "Grow your income", desc: "Prompt packs and content ideas if you're building a page or brand.", icon: Sparkles },
  ];

  return (
    <div>
      <div style={{
        background: `linear-gradient(135deg, ${C.forest}, ${C.forestDark})`,
        borderRadius: 20, padding: "26px 22px", color: "#fff", marginBottom: 28,
        position: "relative", overflow: "hidden",
      }}>
        <div style={{ position: "absolute", top: -30, right: -30, width: 120, height: 120, borderRadius: "50%", background: C.gold, opacity: 0.15 }} />
        <div style={{ fontFamily: monoFont, fontSize: 11, letterSpacing: 1.5, color: C.gold, textTransform: "uppercase" }}>Welcome to</div>
        <h1 style={{ fontFamily: displayFont, fontWeight: 800, fontSize: 30, margin: "6px 0 10px" }}>EkaroWork</h1>
        <p style={{ fontFamily: bodyFont, fontSize: 14.5, lineHeight: 1.6, color: "#EFEAD9", maxWidth: 440 }}>
          "Ekaro" means good morning. Consider this yours — your road from "I want to work remotely" to "I'm getting paid," no jargon, made for Nigerians, one stop at a time.
        </p>
        {result && (
          <div style={{ marginTop: 16, background: "rgba(255,255,255,0.12)", borderRadius: 12, padding: "10px 14px", display: "inline-flex", alignItems: "center", gap: 8 }}>
            <MapPin size={16} color={C.gold} />
            <span style={{ fontFamily: bodyFont, fontSize: 13 }}>Your path: <b>{result.title}</b></span>
          </div>
        )}
      </div>

      <SectionTitle eyebrow="The Trail" title="Your journey, mapped out" sub="Tap any stop to jump straight there." />

      <div style={{ position: "relative", paddingLeft: 6 }}>
        <div style={{ position: "absolute", left: 21, top: 14, bottom: 14, width: 2, background: `repeating-linear-gradient(to bottom, ${C.line} 0, ${C.line} 6px, transparent 6px, transparent 12px)` }} />
        {stops.map((s, i) => {
          const Icon = s.icon;
          return (
            <div key={s.id} onClick={() => goTo(s.id)} style={{
              display: "flex", gap: 16, alignItems: "flex-start", cursor: "pointer",
              padding: "12px 8px", borderRadius: 14, marginBottom: 2,
              transition: "background .15s",
            }}
              onMouseEnter={e => e.currentTarget.style.background = C.greenTint}
              onMouseLeave={e => e.currentTarget.style.background = "transparent"}
            >
              <div style={{
                width: 44, height: 44, borderRadius: "50%", background: C.card, border: `2px solid ${C.forest}`,
                display: "flex", alignItems: "center", justifyContent: "center", flexShrink: 0, zIndex: 1,
              }}>
                <Icon size={19} color={C.forest} />
              </div>
              <div style={{ flex: 1, paddingTop: 4 }}>
                <div style={{ fontFamily: displayFont, fontWeight: 700, fontSize: 15.5, color: C.ink }}>{s.label}</div>
                <div style={{ fontFamily: bodyFont, fontSize: 13, color: C.inkSoft, marginTop: 2, lineHeight: 1.4 }}>{s.desc}</div>
              </div>
              <ChevronRight size={18} color={C.inkSoft} style={{ marginTop: 12 }} />
            </div>
          );
        })}
      </div>
    </div>
  );
}

// ============================================================
// MATCH — Skill matcher quiz
// ============================================================
const QUESTIONS = [
  {
    q: "What do you enjoy most?",
    opts: [
      { t: "Organizing things & helping people stay on top of tasks", k: "va" },
      { t: "Creating photos, reels, or videos", k: "content" },
      { t: "Reading carefully and spotting details others miss", k: "data" },
      { t: "Building and arranging pages/websites", k: "web" },
      { t: "Writing and explaining ideas clearly", k: "write" },
    ],
  },
  {
    q: "Pick a task you'd happily do for free right now:",
    opts: [
      { t: "Manage someone's email or schedule", k: "va" },
      { t: "Make a Reel or TikTok about something you love", k: "content" },
      { t: "Check if a piece of information is true or false", k: "data" },
      { t: "Build a simple page on Wix or Canva", k: "web" },
      { t: "Write a blog post or story", k: "write" },
    ],
  },
  {
    q: "Your strongest skill right now is:",
    opts: [
      { t: "Communication & staying organized", k: "va" },
      { t: "Social media & content creation", k: "content" },
      { t: "Attention to detail / patience", k: "data" },
      { t: "Basic design tools (Wix, Canva, WordPress)", k: "web" },
      { t: "English & storytelling", k: "write" },
    ],
  },
  {
    q: "How do you feel about AI tools like ChatGPT/Claude?",
    opts: [
      { t: "I use them daily, I love this stuff", k: "content" },
      { t: "I'm learning and getting better", k: "va" },
      { t: "I like precise, careful tasks more than creative ones", k: "data" },
      { t: "I prefer visual/design tools", k: "web" },
      { t: "I prefer plain writing over tech tools", k: "write" },
    ],
  },
  {
    q: "What's your goal right now?",
    opts: [
      { t: "I need income fast, even if it's small jobs", k: "va" },
      { t: "I want to build a long-term personal brand", k: "content" },
      { t: "I want steady, structured work I can rely on", k: "data" },
      { t: "I want a skill I can freelance with long-term", k: "web" },
      { t: "I want to get paid to write", k: "write" },
    ],
  },
];

const RESULTS = {
  va: {
    title: "Virtual Assistant",
    desc: "You're organized and people-focused — VA work fits you well. Clients need help with email, scheduling, and admin, and there's steady demand from US/UK small businesses.",
    platforms: ["Upwork", "Fiverr", "Upwork Project Catalog"],
    firstStep: "Build a simple VA resume/CV highlighting organization and communication skills, then create a profile on Upwork and Fiverr this week.",
  },
  content: {
    title: "AI Content Creator",
    desc: "You've got a creative eye and you're comfortable with AI tools. This path is about building an audience on Facebook, YouTube, or TikTok using AI-assisted content.",
    platforms: ["Facebook Pages", "YouTube", "TikTok"],
    firstStep: "Pick one niche, post consistently for 30 days, and use a clear call-to-action on every post to grow followers.",
  },
  data: {
    title: "AI Data Trainer / Annotator",
    desc: "Your patience and attention to detail are exactly what AI companies pay for — labeling, reviewing, and training AI models.",
    platforms: ["DataAnnotation.tech", "Toloka", "Mindrift"],
    firstStep: "Sign up on DataAnnotation.tech or Toloka this week. If you have a specialized background (science, health, law, etc.), Mindrift pays more for expert reviewers.",
  },
  web: {
    title: "Template Website Designer",
    desc: "You like building and arranging — turning templates into working websites for small businesses is a real, sellable skill.",
    platforms: ["Fiverr", "Upwork"],
    firstStep: "Build 2-3 portfolio websites with Wix or WordPress this month, even for practice, then list your service on Fiverr.",
  },
  write: {
    title: "Freelance Writer",
    desc: "You can explain things clearly — that's valuable. Businesses everywhere pay for blog posts, product descriptions, and website copy.",
    platforms: ["Upwork", "Fiverr", "Medium"],
    firstStep: "Write 3 short sample articles (even unpaid ones) to use as your portfolio, then pitch clients on Upwork.",
  },
};

function MatchTab({ onResult }) {
  const [step, setStep] = useState(0);
  const [scores, setScores] = useState({});
  const [result, setResult] = useState(null);

  const answer = (k) => {
    const next = { ...scores, [k]: (scores[k] || 0) + 1 };
    setScores(next);
    if (step + 1 < QUESTIONS.length) {
      setStep(step + 1);
    } else {
      const top = Object.entries(next).sort((a, b) => b[1] - a[1])[0][0];
      const r = RESULTS[top];
      setResult(r);
      onResult(r);
    }
  };

  const restart = () => { setStep(0); setScores({}); setResult(null); };

  if (result) {
    return (
      <div>
        <SectionTitle eyebrow="Your Match" title="Here's your path" />
        <div style={{ background: C.card, border: `1px solid ${C.line}`, borderRadius: 16, padding: 20 }}>
          <div style={{ display: "flex", alignItems: "center", gap: 10, marginBottom: 10 }}>
            <div style={{ width: 38, height: 38, borderRadius: 10, background: C.greenTint, display: "flex", alignItems: "center", justifyContent: "center" }}>
              <Compass size={18} color={C.forest} />
            </div>
            <h3 style={{ fontFamily: displayFont, fontWeight: 800, fontSize: 19, margin: 0, color: C.ink }}>{result.title}</h3>
          </div>
          <p style={{ fontFamily: bodyFont, fontSize: 14, color: C.inkSoft, lineHeight: 1.6 }}>{result.desc}</p>
          <div style={{ marginTop: 14 }}>
            <div style={{ fontFamily: monoFont, fontSize: 11, color: C.terracotta, textTransform: "uppercase", letterSpacing: 1 }}>Where to work</div>
            <div style={{ display: "flex", gap: 8, flexWrap: "wrap", marginTop: 6 }}>
              {result.platforms.map(p => (
                <span key={p} style={{ background: C.greenTint, color: C.forest, fontFamily: bodyFont, fontWeight: 600, fontSize: 12.5, padding: "5px 10px", borderRadius: 20 }}>{p}</span>
              ))}
            </div>
          </div>
          <div style={{ marginTop: 16, background: C.paper, borderRadius: 12, padding: 14, border: `1px dashed ${C.line}` }}>
            <div style={{ fontFamily: monoFont, fontSize: 11, color: C.forest, textTransform: "uppercase", letterSpacing: 1, marginBottom: 4 }}>Your first step</div>
            <div style={{ fontFamily: bodyFont, fontSize: 13.5, color: C.ink, lineHeight: 1.5 }}>{result.firstStep}</div>
          </div>
        </div>
        <button onClick={restart} style={{
          marginTop: 14, background: "none", border: "none", color: C.inkSoft, fontFamily: bodyFont,
          fontSize: 13, cursor: "pointer", display: "flex", alignItems: "center", gap: 6,
        }}>
          <RefreshCw size={13} /> Retake the quiz
        </button>
      </div>
    );
  }

  const q = QUESTIONS[step];
  return (
    <div>
      <SectionTitle eyebrow={`Question ${step + 1} of ${QUESTIONS.length}`} title={q.q} />
      <div style={{ height: 4, background: C.line, borderRadius: 4, marginBottom: 20, overflow: "hidden" }}>
        <div style={{ height: "100%", width: `${((step) / QUESTIONS.length) * 100}%`, background: C.gold, transition: "width .3s" }} />
      </div>
      <div style={{ display: "flex", flexDirection: "column", gap: 10 }}>
        {q.opts.map((o, i) => (
          <button key={i} onClick={() => answer(o.k)} style={{
            textAlign: "left", background: C.card, border: `1px solid ${C.line}`, borderRadius: 12,
            padding: "14px 16px", fontFamily: bodyFont, fontSize: 14, color: C.ink, cursor: "pointer",
            display: "flex", justifyContent: "space-between", alignItems: "center", transition: "border .15s",
          }}
            onMouseEnter={e => e.currentTarget.style.borderColor = C.forest}
            onMouseLeave={e => e.currentTarget.style.borderColor = C.line}
          >
            {o.t} <ChevronRight size={16} color={C.inkSoft} />
          </button>
        ))}
      </div>
    </div>
  );
}

// ============================================================
// JOBS — live feed
// ============================================================
function JobsTab() {
  const [jobs, setJobs] = useState([]);
  const [status, setStatus] = useState("loading"); // loading | ok | error
  const [query, setQuery] = useState("");

  const load = () => {
    setStatus("loading");
    fetch("https://remoteok.com/api")
      .then(r => {
        if (!r.ok) throw new Error("bad response");
        return r.json();
      })
      .then(data => {
        const cleaned = Array.isArray(data) ? data.filter(j => j.id) : [];
        setJobs(cleaned.slice(0, 60));
        setStatus("ok");
      })
      .catch(() => setStatus("error"));
  };

  useEffect(() => { load(); }, []);

  const filtered = useMemo(() => {
    if (!query.trim()) return jobs;
    const q = query.toLowerCase();
    return jobs.filter(j =>
      (j.position || "").toLowerCase().includes(q) ||
      (j.company || "").toLowerCase().includes(q) ||
      (Array.isArray(j.tags) ? j.tags.join(" ") : "").toLowerCase().includes(q)
    );
  }, [jobs, query]);

  const fallbackLinks = [
    { name: "Remotive", url: "https://remotive.com" },
    { name: "We Work Remotely", url: "https://weworkremotely.com" },
    { name: "NaijaRemoteJobs", url: "https://naijaremotejobs.com" },
    { name: "Jobberman (Remote filter)", url: "https://www.jobberman.com" },
  ];

  return (
    <div>
      <SectionTitle eyebrow="Live Feed" title="Remote jobs, right now" sub="Pulled live from the web. Search by role, skill, or company." />
      <div style={{ display: "flex", gap: 8, marginBottom: 16 }}>
        <div style={{ flex: 1, display: "flex", alignItems: "center", background: C.card, border: `1px solid ${C.line}`, borderRadius: 10, padding: "0 12px" }}>
          <Search size={15} color={C.inkSoft} />
          <input
            value={query} onChange={e => setQuery(e.target.value)}
            placeholder="e.g. writer, virtual assistant, design"
            style={{ border: "none", outline: "none", padding: "10px 8px", fontFamily: bodyFont, fontSize: 13.5, flex: 1, background: "transparent" }}
          />
        </div>
        <button onClick={load} style={{ background: C.forest, border: "none", borderRadius: 10, padding: "0 14px", cursor: "pointer" }}>
          <RefreshCw size={16} color="#fff" />
        </button>
      </div>

      {status === "loading" && (
        <div style={{ display: "flex", alignItems: "center", gap: 8, color: C.inkSoft, fontFamily: bodyFont, fontSize: 14, padding: 30, justifyContent: "center" }}>
          <Loader2 size={18} className="spin" style={{ animation: "spin 1s linear infinite" }} /> Loading live jobs…
        </div>
      )}

      {status === "error" && (
        <div style={{ background: C.card, border: `1px solid ${C.line}`, borderRadius: 14, padding: 18 }}>
          <p style={{ fontFamily: bodyFont, fontSize: 13.5, color: C.inkSoft, marginBottom: 10 }}>
            Couldn't load live listings right now. Try these trusted job boards directly:
          </p>
          {fallbackLinks.map(f => (
            <a key={f.name} href={f.url} target="_blank" rel="noopener noreferrer" style={{
              display: "flex", justifyContent: "space-between", alignItems: "center",
              padding: "10px 4px", borderTop: `1px solid ${C.line}`, textDecoration: "none",
              color: C.ink, fontFamily: bodyFont, fontSize: 13.5, fontWeight: 600,
            }}>
              {f.name} <ExternalLink size={14} color={C.inkSoft} />
            </a>
          ))}
        </div>
      )}

      {status === "ok" && (
        <div style={{ display: "flex", flexDirection: "column", gap: 10 }}>
          {filtered.length === 0 && <p style={{ fontFamily: bodyFont, color: C.inkSoft, fontSize: 13.5 }}>No matches — try a different search word.</p>}
          {filtered.map(j => (
            <a key={j.id} href={j.url || `https://remoteok.com/remote-jobs/${j.id}`} target="_blank" rel="noopener noreferrer"
              style={{ textDecoration: "none", background: C.card, border: `1px solid ${C.line}`, borderRadius: 14, padding: 14, display: "block" }}>
              <div style={{ display: "flex", justifyContent: "space-between", gap: 10 }}>
                <div>
                  <div style={{ fontFamily: displayFont, fontWeight: 700, fontSize: 14.5, color: C.ink }}>{j.position}</div>
                  <div style={{ fontFamily: bodyFont, fontSize: 13, color: C.inkSoft, marginTop: 2 }}>{j.company}{j.location ? ` · ${j.location}` : ""}</div>
                </div>
                <ExternalLink size={15} color={C.inkSoft} style={{ flexShrink: 0, marginTop: 3 }} />
              </div>
              {Array.isArray(j.tags) && j.tags.length > 0 && (
                <div style={{ display: "flex", gap: 6, flexWrap: "wrap", marginTop: 8 }}>
                  {j.tags.slice(0, 4).map(t => (
                    <span key={t} style={{ background: C.greenTint, color: C.forest, fontFamily: monoFont, fontSize: 10.5, padding: "3px 8px", borderRadius: 20 }}>{t}</span>
                  ))}
                </div>
              )}
            </a>
          ))}
        </div>
      )}
    </div>
  );
}

// ============================================================
// TOOLKIT — CV Builder + Platform/Payment guide
// ============================================================
function CVBuilder() {
  const [f, setF] = useState({ name: "", role: "", email: "", phone: "", location: "", skills: "", experience: "", education: "" });
  const set = (k) => (e) => setF({ ...f, [k]: e.target.value });

  const cvText = useMemo(() => {
    const lines = [];
    lines.push((f.name || "Your Name").toUpperCase());
    lines.push(f.role || "Target Role");
    lines.push([f.email, f.phone, f.location].filter(Boolean).join(" | "));
    lines.push("");
    if (f.skills) { lines.push("SKILLS"); lines.push(f.skills.split(",").map(s => s.trim()).filter(Boolean).join(" · ")); lines.push(""); }
    if (f.experience) { lines.push("EXPERIENCE"); f.experience.split("\n").filter(Boolean).forEach(l => lines.push("• " + l.trim())); lines.push(""); }
    if (f.education) { lines.push("EDUCATION"); f.education.split("\n").filter(Boolean).forEach(l => lines.push("• " + l.trim())); }
    return lines.join("\n");
  }, [f]);

  const fields = [
    { k: "name", label: "Full name", ph: "e.g. Amaka Obi" },
    { k: "role", label: "Target role", ph: "e.g. Virtual Assistant" },
    { k: "email", label: "Email", ph: "you@email.com" },
    { k: "phone", label: "Phone", ph: "+234…" },
    { k: "location", label: "Location", ph: "e.g. Enugu, Nigeria" },
  ];

  return (
    <div>
      <div style={{ display: "grid", gridTemplateColumns: "1fr 1fr", gap: 10, marginBottom: 10 }}>
        {fields.map(fl => (
          <div key={fl.k} style={{ gridColumn: fl.k === "name" || fl.k === "role" ? "span 2" : "span 1" }}>
            <label style={{ fontFamily: monoFont, fontSize: 10.5, color: C.inkSoft, textTransform: "uppercase" }}>{fl.label}</label>
            <input value={f[fl.k]} onChange={set(fl.k)} placeholder={fl.ph} style={inputStyle} />
          </div>
        ))}
      </div>
      <label style={labelStyle}>Skills (comma separated)</label>
      <input value={f.skills} onChange={set("skills")} placeholder="e.g. Email management, Scheduling, Canva" style={inputStyle} />
      <label style={labelStyle}>Experience (one line each)</label>
      <textarea value={f.experience} onChange={set("experience")} placeholder="e.g. Coordinated events for a 200-member university club" rows={3} style={{ ...inputStyle, resize: "vertical" }} />
      <label style={labelStyle}>Education (optional, one line each)</label>
      <textarea value={f.education} onChange={set("education")} placeholder="e.g. B.Sc, ESUT — expected 2028" rows={2} style={{ ...inputStyle, resize: "vertical" }} />

      <div style={{ marginTop: 16, background: C.paper, border: `1px dashed ${C.line}`, borderRadius: 12, padding: 16 }}>
        <div style={{ display: "flex", justifyContent: "space-between", alignItems: "center", marginBottom: 8 }}>
          <div style={{ fontFamily: monoFont, fontSize: 11, color: C.forest, textTransform: "uppercase", letterSpacing: 1 }}>Preview</div>
          <CopyBtn text={cvText} small />
        </div>
        <pre style={{ fontFamily: monoFont, fontSize: 12, color: C.ink, whiteSpace: "pre-wrap", margin: 0, lineHeight: 1.6 }}>{cvText}</pre>
      </div>
    </div>
  );
}

const inputStyle = {
  width: "100%", boxSizing: "border-box", border: `1px solid ${C.line}`, borderRadius: 8,
  padding: "9px 11px", fontFamily: bodyFont, fontSize: 13.5, marginBottom: 10, background: C.card, color: C.ink,
};
const labelStyle = { fontFamily: monoFont, fontSize: 10.5, color: C.inkSoft, textTransform: "uppercase", display: "block", marginBottom: 4 };

const GUIDE = [
  { name: "Upwork", body: "Best for VA, writing, and design gigs from US/UK clients. Getting your first job is the hardest part — apply to smaller jobs first to build reviews. Connects (credits to apply) are limited, so write focused proposals rather than applying everywhere." },
  { name: "Fiverr", body: "You create 'gigs' and clients come to you — good alongside Upwork. Clear gig titles and a few strong sample images matter more than a long description." },
  { name: "Freelancer.com", body: "Similar to Upwork with more entry-level jobs and contests. Good for building initial reviews while your Upwork profile is new." },
  { name: "PeoplePerHour", body: "UK-focused freelance platform. 'Hourlies' (fixed-price mini services) work well for quick wins in writing, design, and VA tasks." },
  { name: "Contra", body: "Commission-free freelance platform, growing fast for designers, writers, and marketers who want to keep 100% of what they earn." },
  { name: "LinkedIn", body: "Not just for CVs — post about your skills, comment on hiring posts, and use the 'Open to Work' setting. Many remote roles are filled here before they're ever posted publicly." },
  { name: "DataAnnotation.tech / Toloka", body: "Pay for labeling and reviewing AI training data. Sign up is usually straightforward; work is flexible and part-time friendly. Prefer these over platforms with documented pay/labor issues for Nigerian workers." },
  { name: "Mindrift", body: "Pays well for domain-expert AI training tasks (science, health, law, coding). A specialized background is a real advantage here." },
  { name: "Appen", body: "Another AI data/content evaluation platform with recurring project-based work. Qualification tests are required before you start." },
  { name: "Turing", body: "Focused on vetted remote software/tech roles for experienced developers — worth exploring if you build technical skills later." },
  { name: "Payoneer (getting paid)", body: "1) Sign up at payoneer.com with a valid ID. 2) Verify your account (can take a few days). 3) Link it as your payment method on Upwork/Fiverr. 4) Withdraw to your Nigerian bank account — check current transfer fees before withdrawing." },
  { name: "Wise (alternative payout option)", body: "Good alternative to Payoneer for receiving USD/GBP/EUR and converting to Naira, often with lower fees for certain currencies. Compare both before committing to one." },
];

function PlatformGuide() {
  const [open, setOpen] = useState(null);
  return (
    <div style={{ marginTop: 26 }}>
      <SectionTitle eyebrow="Guide" title="Platforms & getting paid" />
      {GUIDE.map((g, i) => (
        <div key={g.name} style={{ borderBottom: `1px solid ${C.line}` }}>
          <button onClick={() => setOpen(open === i ? null : i)} style={{
            width: "100%", background: "none", border: "none", padding: "14px 4px", cursor: "pointer",
            display: "flex", justifyContent: "space-between", alignItems: "center",
          }}>
            <span style={{ fontFamily: displayFont, fontWeight: 700, fontSize: 14.5, color: C.ink }}>{g.name}</span>
            <ChevronDown size={17} color={C.inkSoft} style={{ transform: open === i ? "rotate(180deg)" : "none", transition: "transform .2s" }} />
          </button>
          {open === i && <p style={{ fontFamily: bodyFont, fontSize: 13.5, color: C.inkSoft, lineHeight: 1.6, padding: "0 4px 14px" }}>{g.body}</p>}
        </div>
      ))}
    </div>
  );
}

const RED_FLAGS = [
  { title: "Any job asking you to pay first", body: "Real employers never ask you to pay for 'training materials', a 'starter kit', software, or a 'registration fee' before you start. If money is supposed to flow toward you and someone asks you to send money first, stop." },
  { title: "Fake check / overpayment scams", body: "A 'client' sends a check or transfer for more than agreed and asks you to refund the difference. The original payment later bounces and you lose the refunded money. Never refund money — wait for funds to fully clear first, and be suspicious of any overpayment." },
  { title: "Too-good-to-be-true pay for zero skill", body: "'Earn $500/day typing from home, no experience' is almost always a scam or a pyramid scheme. Real remote pay matches real skill level — be skeptical of huge numbers for tiny effort." },
  { title: "Requests for OTP, bank PIN, or full card details", body: "No legitimate platform, client, or 'support agent' will ever ask for your one-time password, ATM PIN, or full card number by chat, call, or email. Anyone asking is trying to steal from you." },
  { title: "Lookalike websites and links", body: "Scammers clone Upwork, Payoneer, and bank login pages. Before entering a password, check the URL is exactly correct (e.g. upwork.com, not upwork-jobs.com or a shortened link) and type it yourself instead of clicking unknown links." },
  { title: "Pressure to move off the official platform fast", body: "A client who insists on moving to WhatsApp/Telegram and paying 'outside the platform' immediately removes your protection if something goes wrong. Be extra cautious, especially early on." },
  { title: "Vague job descriptions with instant offers", body: "If you're 'hired' without any real interview or skill check, for a role that's vaguely described, treat it as a red flag rather than good luck." },
];

const SAFETY_TIPS = [
  "Use a different, strong password for every platform (Upwork, Payoneer, email, bank) — a password manager makes this easy.",
  "Turn on two-factor authentication (2FA) on your email, Payoneer, and freelance platform accounts.",
  "Use the official app or type the website address yourself — don't log in through links sent in messages or emails.",
  "Keep your CV and portfolio free of sensitive personal data like your full ID number or bank details — clients don't need these to hire you.",
  "Verify a company is real before engaging deeply: search their name plus 'reviews' or 'scam', check LinkedIn for real employees.",
  "Never share your screen or remote-access your device for a 'job task' — this is a common way scammers install malware or steal information.",
  "If it feels rushed, secretive, or too generous, slow down and verify before acting.",
];

function StaySafe() {
  return (
    <div style={{ marginTop: 26 }}>
      <SectionTitle eyebrow="Protect Yourself" title="Scams to avoid" sub="Remote work attracts real opportunity — and real scammers. Know these patterns." />
      <div style={{ display: "flex", flexDirection: "column", gap: 10, marginBottom: 26 }}>
        {RED_FLAGS.map((r, i) => (
          <div key={i} style={{ background: C.card, border: `1px solid ${C.line}`, borderLeft: `4px solid ${C.terracotta}`, borderRadius: 10, padding: 14 }}>
            <div style={{ display: "flex", alignItems: "center", gap: 8, marginBottom: 4 }}>
              <AlertTriangle size={15} color={C.terracotta} />
              <span style={{ fontFamily: displayFont, fontWeight: 700, fontSize: 14, color: C.ink }}>{r.title}</span>
            </div>
            <p style={{ fontFamily: bodyFont, fontSize: 13, color: C.inkSoft, lineHeight: 1.55, margin: 0 }}>{r.body}</p>
          </div>
        ))}
      </div>

      <SectionTitle eyebrow="Account Security" title="Keep your accounts locked down" />
      <div style={{ background: C.greenTint, borderRadius: 14, padding: 16 }}>
        {SAFETY_TIPS.map((t, i) => (
          <div key={i} style={{ display: "flex", gap: 10, alignItems: "flex-start", marginBottom: i < SAFETY_TIPS.length - 1 ? 12 : 0 }}>
            <Lock size={15} color={C.forest} style={{ marginTop: 2, flexShrink: 0 }} />
            <span style={{ fontFamily: bodyFont, fontSize: 13, color: C.ink, lineHeight: 1.5 }}>{t}</span>
          </div>
        ))}
      </div>
    </div>
  );
}

function ToolkitTab() {
  const [sub, setSub] = useState("cv");
  const tabs = [
    { id: "cv", label: "CV Builder", icon: FileText },
    { id: "guide", label: "Payment Guide", icon: CreditCard },
    { id: "safety", label: "Stay Safe", icon: Shield },
  ];
  return (
    <div>
      <SectionTitle eyebrow="Toolkit" title="Build your CV & get set up" />
      <div style={{ display: "flex", gap: 8, marginBottom: 20, flexWrap: "wrap" }}>
        {tabs.map(t => (
          <button key={t.id} onClick={() => setSub(t.id)} style={{
            display: "flex", alignItems: "center", gap: 6, padding: "8px 14px", borderRadius: 20,
            border: `1px solid ${sub === t.id ? C.forest : C.line}`, background: sub === t.id ? C.forest : C.card,
            color: sub === t.id ? "#fff" : C.ink, fontFamily: bodyFont, fontWeight: 600, fontSize: 13, cursor: "pointer",
          }}>
            <t.icon size={14} /> {t.label}
          </button>
        ))}
      </div>
      {sub === "cv" && <CVBuilder />}
      {sub === "guide" && <PlatformGuide />}
      {sub === "safety" && <StaySafe />}
    </div>
  );
}

// ============================================================
// GROW — Prompt Vault + Content Idea Generator
// ============================================================
const PROMPTS = [
  { cat: "Reels & Captions", title: "Scroll-stopping Reels caption", text: "Write a scroll-stopping Facebook Reels caption about [TOPIC] for a Nigerian audience. Start with a bold hook in the first line, keep it conversational, and end with a question that invites comments." },
  { cat: "Reels & Captions", title: "Debate-style caption", text: "Write a short caption about [TOPIC] that takes a mild, debatable stance to spark disagreement in the comments, written in a friendly, non-preachy tone for a Nigerian Facebook audience." },
  { cat: "YouTube", title: "Video hook + outline", text: "Give me a 10-second spoken hook and a 5-point outline for a YouTube video about [TOPIC], aimed at Nigerian beginners with no prior knowledge. Use simple, conversational English." },
  { cat: "Career", title: "CV bullet point rewriter", text: "Rewrite this experience into a strong CV bullet point using an action verb and a result, in plain English: [PASTE EXPERIENCE]." },
  { cat: "Business", title: "Small business idea check", text: "I have [SKILL/RESOURCE]. Suggest 3 realistic small business or side-income ideas I could start in Nigeria with less than [BUDGET], and one first step for each." },
];

function PromptVault() {
  return (
    <div>
      <SectionTitle eyebrow="Free" title="Prompt Vault" sub="Copy, paste into any AI tool, swap the [BRACKETS] for your topic." />
      <div style={{ display: "flex", flexDirection: "column", gap: 10 }}>
        {PROMPTS.map((p, i) => (
          <div key={i} style={{ background: C.card, border: `1px solid ${C.line}`, borderRadius: 12, padding: 14 }}>
            <div style={{ display: "flex", justifyContent: "space-between", alignItems: "flex-start", gap: 8 }}>
              <div>
                <span style={{ fontFamily: monoFont, fontSize: 10, color: C.terracotta, textTransform: "uppercase" }}>{p.cat}</span>
                <div style={{ fontFamily: displayFont, fontWeight: 700, fontSize: 14, color: C.ink, marginTop: 2 }}>{p.title}</div>
              </div>
              <CopyBtn text={p.text} small />
            </div>
            <p style={{ fontFamily: bodyFont, fontSize: 12.5, color: C.inkSoft, marginTop: 8, lineHeight: 1.5 }}>{p.text}</p>
          </div>
        ))}
      </div>
      <div style={{ marginTop: 14, textAlign: "center", padding: 14, border: `1px dashed ${C.line}`, borderRadius: 12 }}>
        <span style={{ fontFamily: bodyFont, fontSize: 12.5, color: C.inkSoft }}>More prompt packs coming as paid add-ons 🔒</span>
      </div>
    </div>
  );
}

const NICHES = {
  "Remote Work Tips": {
    hooks: ["You don't need a degree to earn in dollars — here's proof.", "This one mistake is why your Upwork profile isn't getting hired.", "Nobody tells beginners this about remote work in Nigeria."],
    ctas: ["Drop 'GUIDE' in the comments and I'll send you the steps.", "Agree or disagree? Say it in the comments.", "Follow for a new remote work tip every week."],
  },
  "AI Tools": {
    hooks: ["This AI tool just replaced 3 hours of my work.", "Most people are using ChatGPT wrong — here's the fix.", "I asked AI to build me a side income. Here's what happened."],
    ctas: ["Comment 'PROMPT' and I'll send you the exact one I used.", "Which AI tool do you use most? Let's argue about it below.", "Follow if you want more AI tips like this."],
  },
  "Football / World Cup": {
    hooks: ["This player is more important than people admit.", "Unpopular opinion about this match — fight me in the comments.", "The stat nobody is talking about from last night's game."],
    ctas: ["Who do you think wins? Comment your pick.", "Tag someone who needs to see this.", "Follow for daily World Cup takes."],
  },
  "Productivity": {
    hooks: ["I tried this 'lazy' productivity method for a week.", "Stop doing this if you want to get more done.", "This changed how I plan my whole week."],
    ctas: ["Comment 'PLAN' and I'll share my template.", "What's your biggest time-waster? Say it below.", "Follow for more simple productivity ideas."],
  },
};

function ContentIdeaGen() {
  const [niche, setNiche] = useState("Remote Work Tips");
  const [ideas, setIdeas] = useState([]);

  const generate = () => {
    const n = NICHES[niche];
    const picks = [];
    const usedH = new Set(), usedC = new Set();
    for (let i = 0; i < 3; i++) {
      let h, c;
      do { h = n.hooks[Math.floor(Math.random() * n.hooks.length)]; } while (usedH.has(h) && usedH.size < n.hooks.length);
      do { c = n.ctas[Math.floor(Math.random() * n.ctas.length)]; } while (usedC.has(c) && usedC.size < n.ctas.length);
      usedH.add(h); usedC.add(c);
      picks.push({ hook: h, cta: c });
    }
    setIdeas(picks);
  };

  return (
    <div style={{ marginTop: 28 }}>
      <SectionTitle eyebrow="Generator" title="Content Idea Generator" sub="Pick a niche, get hook + follow-CTA pairs ready to post." />
      <div style={{ display: "flex", gap: 8, marginBottom: 14 }}>
        <select value={niche} onChange={e => setNiche(e.target.value)} style={{ ...inputStyle, marginBottom: 0, flex: 1 }}>
          {Object.keys(NICHES).map(n => <option key={n}>{n}</option>)}
        </select>
        <button onClick={generate} style={{
          background: C.gold, border: "none", borderRadius: 8, padding: "0 16px", cursor: "pointer",
          display: "flex", alignItems: "center", gap: 6, fontFamily: bodyFont, fontWeight: 700, fontSize: 13, color: C.ink,
        }}>
          <Wand2 size={15} /> Generate
        </button>
      </div>
      <div style={{ display: "flex", flexDirection: "column", gap: 10 }}>
        {ideas.map((idea, i) => {
          const full = `${idea.hook}\n\n[Line 2: Follow for more ${niche} content]\n\n${idea.cta}`;
          return (
            <div key={i} style={{ background: C.card, border: `1px solid ${C.line}`, borderRadius: 12, padding: 14 }}>
              <div style={{ fontFamily: displayFont, fontWeight: 700, fontSize: 14, color: C.ink }}>Hook: {idea.hook}</div>
              <div style={{ fontFamily: bodyFont, fontSize: 12.5, color: C.inkSoft, marginTop: 6 }}>CTA: {idea.cta}</div>
              <div style={{ marginTop: 10 }}><CopyBtn text={full} small /></div>
            </div>
          );
        })}
      </div>
    </div>
  );
}

function GrowTab() {
  const [sub, setSub] = useState("vault");
  return (
    <div>
      <div style={{ display: "flex", gap: 8, marginBottom: 20 }}>
        {[{ id: "vault", label: "Prompt Vault", icon: BookOpen }, { id: "ideas", label: "Content Ideas", icon: Sparkles }].map(t => (
          <button key={t.id} onClick={() => setSub(t.id)} style={{
            display: "flex", alignItems: "center", gap: 6, padding: "8px 14px", borderRadius: 20,
            border: `1px solid ${sub === t.id ? C.forest : C.line}`, background: sub === t.id ? C.forest : C.card,
            color: sub === t.id ? "#fff" : C.ink, fontFamily: bodyFont, fontWeight: 600, fontSize: 13, cursor: "pointer",
          }}>
            <t.icon size={14} /> {t.label}
          </button>
        ))}
      </div>
      {sub === "vault" ? <PromptVault /> : <ContentIdeaGen />}
    </div>
  );
}

// ============================================================
// APP SHELL
// ============================================================
export default function App() {
  const [tab, setTab] = useState("home");
  const [result, setResult] = useState(null);

  const NAV = [
    { id: "home", label: "Home", icon: Home },
    { id: "match", label: "Match", icon: Compass },
    { id: "jobs", label: "Jobs", icon: Briefcase },
    { id: "toolkit", label: "Toolkit", icon: Wrench },
    { id: "grow", label: "Grow", icon: Sparkles },
  ];

  return (
    <div style={{ fontFamily: bodyFont, background: C.paper, minHeight: "100vh", color: C.ink }}>
      <style>{`
        ${FONT_IMPORT}
        * { -webkit-tap-highlight-color: transparent; }
        input:focus, textarea:focus, select:focus { outline: 2px solid ${C.gold}; }
        @keyframes spin { to { transform: rotate(360deg); } }
      `}</style>

      <div style={{ height: 4, background: `linear-gradient(90deg, ${C.forest}, ${C.gold})` }} />

      <div style={{ maxWidth: 480, margin: "0 auto", padding: "20px 18px 100px" }}>
        {tab === "home" && <HomeTab goTo={setTab} result={result} />}
        {tab === "match" && <MatchTab onResult={setResult} />}
        {tab === "jobs" && <JobsTab />}
        {tab === "toolkit" && <ToolkitTab />}
        {tab === "grow" && <GrowTab />}
      </div>

      <div style={{
        position: "fixed", bottom: 0, left: 0, right: 0, background: "#fff",
        borderTop: `1px solid ${C.line}`, display: "flex", justifyContent: "space-around",
        padding: "8px 4px 10px", maxWidth: 480, margin: "0 auto",
      }}>
        {NAV.map(n => {
          const active = tab === n.id;
          return (
            <button key={n.id} onClick={() => setTab(n.id)} style={{
              background: "none", border: "none", display: "flex", flexDirection: "column",
              alignItems: "center", gap: 3, cursor: "pointer", padding: "4px 10px",
              color: active ? C.forest : C.inkSoft,
            }}>
              <n.icon size={20} strokeWidth={active ? 2.4 : 1.8} />
              <span style={{ fontFamily: bodyFont, fontSize: 10.5, fontWeight: active ? 700 : 500 }}>{n.label}</span>
            </button>
          );
        })}
      </div>
    </div>
  );
}
