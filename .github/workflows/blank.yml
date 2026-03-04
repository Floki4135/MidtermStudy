import { useState, useEffect, useCallback } from "react";

const sections = [
  {
    title: "Ethical Hacking Foundations",
    icon: "🛡️",
    questions: [
      { q: "Ethical hacking requires written _____ before testing begins.", a: "authorization" },
      { q: "_____ hat hackers operate with permission and legal authorization.", a: "white" },
      { q: "A hacker motivated by fame who uses prewritten tools is called a _____.", a: "script kiddie" },
      { q: "Ethical hackers identify vulnerabilities and report them _____.", a: "responsibly" },
      { q: "_____ hat hackers break into systems without permission and with malicious intent.", a: "black" },
      { q: "_____ hat hackers may act without authorization but without malicious intent, sometimes reporting bugs.", a: "gray" },
      { q: "A weakness in a system that can be exploited is called a _____.", a: "vulnerability" },
      { q: "A piece of code or technique that takes advantage of a vulnerability is called an _____.", a: "exploit" },
      { q: "A potential danger that could exploit a vulnerability is called a _____.", a: "threat" },
      { q: "The CIA triad stands for Confidentiality, Integrity, and _____.", a: "availability" },
      { q: "A _____ disclosure policy means reporting vulnerabilities to the vendor before going public.", a: "responsible" },
    ],
  },
  {
    title: "Penetration Testing & Legal",
    icon: "⚖️",
    questions: [
      { q: "A penetration test is an authorized simulated _____.", a: "cyberattack" },
      { q: "The first phase of the pen test life cycle is _____.", a: "planning & authorization" },
      { q: "The document that defines testing boundaries is the _____.", a: "scope of work" },
      { q: "Unauthorized access may violate the _____ (CFAA).", a: "computer fraud and abuse act" },
      { q: "Packet interception without permission may violate the _____ (ECPA).", a: "electronic communications privacy act" },
      { q: "The most valuable deliverable of a pen test is the _____.", a: "final report" },
      { q: "The CFAA is codified under _____ U.S.C. § 1030.", a: "18" },
      { q: "The ECPA is codified under 18 U.S.C. § _____.", a: "2511" },
      { q: "Identity theft and fraud laws fall under 18 U.S.C. § _____.", a: "1028" },
      { q: "Wire fraud, sometimes applied to hacking, falls under 18 U.S.C. § _____.", a: "1343" },
      { q: "Under U.S. law, _____ does not matter — unauthorized access is still illegal.", a: "intent" },
      { q: "Victims of unauthorized testing can file _____ lawsuits even without criminal charges.", a: "civil" },
      { q: "A _____ box test gives the tester no prior knowledge of the target environment.", a: "black" },
      { q: "A _____ box test gives the tester full knowledge including source code and network diagrams.", a: "white" },
      { q: "A _____ box test gives the tester partial knowledge, simulating an insider or semi-trusted attacker.", a: "gray" },
      { q: "The pen test team simulating attackers is called the _____ team.", a: "red" },
      { q: "The team defending the network during an exercise is the _____ team.", a: "blue" },
      { q: "A _____ team combines offensive and defensive skills to improve both.", a: "purple" },
    ],
  },
  {
    title: "Pen Test Lifecycle & Reports",
    icon: "📋",
    questions: [
      { q: "The 6 pen test phases in order: Planning, Reconnaissance, Scanning, Exploitation, _____, Reporting.", a: "post-exploitation" },
      { q: "During post-exploitation, testers attempt privilege escalation and _____ movement.", a: "lateral" },
      { q: "The pen test report section written for leadership (not technical staff) is the _____.", a: "executive summary" },
      { q: "The report section listing systems tested, dates, and rules of engagement is _____.", a: "scope & methodology" },
      { q: "Vulnerabilities in the report include description, evidence, and a _____ rating.", a: "severity" },
      { q: "Remediation recommendations should be prioritized based on _____.", a: "risk" },
      { q: "The optional report section containing tools used and raw output is the _____.", a: "appendices" },
      { q: "Four common pen test findings: weak passwords, unpatched systems, misconfigurations, and excessive _____.", a: "privileges" },
      { q: "Four required pen test documents: written authorization, scope of work, rules of engagement, and _____.", a: "non-disclosure agreement" },
      { q: "Risks of unauthorized testing include criminal charges, civil lawsuits, and _____ loss.", a: "certification" },
      { q: "The impact analysis section describes what an attacker could realistically _____ if the vulnerability were exploited.", a: "achieve" },
      { q: "During Phase 1, the team must define scope, obtain written permission, set rules of engagement, and establish _____ contacts.", a: "emergency" },
    ],
  },
  {
    title: "Pen Test History",
    icon: "📜",
    questions: [
      { q: "In 1970, the _____ Corporation published 'Security Controls for Computer Systems.'", a: "RAND" },
      { q: "In the 1980s, the U.S. DoD formed _____ Teams — trusted experts who tested security with authorization.", a: "tiger" },
      { q: "The _____ Worm in the late 1980s revealed large-scale cyber risk and expanded pen testing beyond government.", a: "Morris" },
      { q: "Three modern pen testing standards: NIST SP 800-115, OSSTMM, and _____.", a: "PTES" },
      { q: "Penetration testing originated from _____ and military efforts, not criminal hacking.", a: "government" },
      { q: "In the 1960s–70s, risks were identified in early _____-sharing computer systems.", a: "time" },
    ],
  },
  {
    title: "Reconnaissance & OSINT",
    icon: "🔍",
    questions: [
      { q: "OSINT stands for _____.", a: "open source intelligence" },
      { q: "Reconnaissance involves locating, gathering, identifying, _____ information about a target.", a: "recording" },
      { q: "_____ reconnaissance has a low risk of detection.", a: "passive" },
      { q: "_____ reconnaissance involves direct engagement with the target.", a: "active" },
      { q: "OSINT is about _____, not just collecting data — individual facts must be combined and interpreted.", a: "context" },
      { q: "OSINT risk is _____ — small public details become dangerous when aggregated over time.", a: "cumulative" },
      { q: "OSINT findings must be documented and _____ with clear sourcing and timestamps.", a: "reproducible" },
      { q: "Internet research sources for recon include company websites, social media, discussion groups, financial reports, and _____.", a: "news articles" },
      { q: "Information gathering targets include contact names, phone numbers, email addresses, security systems, and technical _____.", a: "infrastructure" },
      { q: "OSINT exposes organizational behavior through job postings, social media, and _____ documents.", a: "public" },
      { q: "The _____ database provides domain registration info including registrant name, email, and name servers.", a: "WHOIS" },
      { q: "Using advanced search operators like 'filetype:' and 'inurl:' to find exposed data is called Google _____.", a: "dorking" },
      { q: "The search engine _____ indexes internet-connected devices like webcams, servers, and IoT, making it useful for recon.", a: "Shodan" },
      { q: "_____ is an OSINT tool that visually maps relationships between people, domains, IPs, and organizations.", a: "Maltego" },
      { q: "The tool _____ automates gathering emails, subdomains, and names from public sources for a target domain.", a: "theHarvester" },
      { q: "A DNS _____ record maps a domain name to an IPv4 address.", a: "A" },
      { q: "A DNS _____ record identifies the mail server responsible for receiving email for a domain.", a: "MX" },
      { q: "A DNS _____ record maps a domain to another domain name (alias).", a: "CNAME" },
      { q: "The command-line tool used to query DNS records is _____ (or dig).", a: "nslookup" },
      { q: "The Wayback Machine at _____ lets you view archived versions of websites for passive recon.", a: "archive.org" },
    ],
  },
  {
    title: "Social Engineering",
    icon: "🎭",
    questions: [
      { q: "Social engineering relies on psychological _____.", a: "manipulation" },
      { q: "Creating a believable story to extract information is called _____.", a: "pretexting" },
      { q: "Pretending to be a supervisor to gain access is _____.", a: "authority impersonation" },
      { q: "_____ is a form of physical social engineering where someone follows an employee into a secure area.", a: "tailgating" },
      { q: "Kevin _____ is one of the most famous social engineers, who relied on people rather than malware.", a: "Mitnick" },
      { q: "Five psychological triggers that make social engineering work: trust, authority, urgency, fear, and _____.", a: "helpfulness" },
      { q: "Building friendly conversation and shared frustrations to lower suspicion is called _____ building.", a: "rapport" },
      { q: "Collecting small details over time with no single red flag, then aggregating them, is information _____.", a: "harvesting" },
      { q: "Voice-based phishing conducted over the phone is called _____.", a: "vishing" },
      { q: "Using partial technical language and confidence to make victims hesitate is called technical _____ abuse.", a: "jargon" },
      { q: "Recovering discarded data from trash to enhance future attacks is called _____.", a: "dumpster diving" },
      { q: "Mitnick's method: gather information, build trust, exploit _____, avoid technical detection.", a: "processes" },
      { q: "Phishing via SMS text messages is called _____.", a: "smishing" },
      { q: "Leaving infected USB drives in public areas hoping someone plugs one in is called a _____ attack.", a: "baiting" },
      { q: "A _____ hole attack compromises a website frequently visited by the target group.", a: "watering" },
      { q: "Repeatedly sending MFA push notifications hoping the victim approves one is called MFA _____ attack.", a: "fatigue" },
      { q: "The best defense against social engineering is security _____ training for all employees.", a: "awareness" },
      { q: "The principle of _____ means only granting users the minimum access they need to do their job.", a: "least privilege" },
      { q: "_____ impersonation involves wearing a uniform or carrying equipment to blend in and gain physical access.", a: "uniform" },
      { q: "A proper document _____ policy (like shredding) prevents dumpster diving attacks.", a: "disposal" },
    ],
  },
  {
    title: "Phishing & OSINT-Driven Attacks",
    icon: "🎣",
    questions: [
      { q: "A highly targeted phishing email using personal details about the victim is called _____ phishing.", a: "spear" },
      { q: "Spear phishing targeting high-level executives specifically is called _____.", a: "whaling" },
      { q: "Business Email Compromise (BEC) often targets _____ staff to exploit approval chains and vendor payments.", a: "finance" },
      { q: "OSINT reduces attacker _____, improving the credibility and timing of attacks.", a: "guesswork" },
      { q: "OSINT turns generic attacks into _____ ones.", a: "targeted" },
      { q: "Two modern social engineering threats using the same psychology but new tools: AI phishing and _____ voice attacks.", a: "deepfake" },
      { q: "Eight phishing red flags include: sender address, generic greeting, urgent language, spelling errors, suspicious links, unsolicited attachments, no secure connection, and requests for _____ info.", a: "personal" },
      { q: "Attackers use _____ patterns and SSO platforms for credential harvesting and account takeover.", a: "username" },
      { q: "A phishing email that appears to come from a known contact using a spoofed or compromised account exploits _____.", a: "trust" },
      { q: "Before clicking a link in an email, you should _____ over it to reveal the actual URL destination.", a: "hover" },
    ],
  },
  {
    title: "Scanning, Enumeration & Nmap",
    icon: "📡",
    questions: [
      { q: "Scanning identifies live hosts and open _____.", a: "ports" },
      { q: "Enumeration extracts deeper information such as _____.", a: "service versions" },
      { q: "Ports 0–1023 are called _____ ports.", a: "well-known" },
      { q: "The Nmap switch used for service version detection is _____.", a: "-sV" },
      { q: "The Nmap switch used for operating system detection is _____.", a: "-O" },
      { q: "The Nmap switch that performs an aggressive scan is _____.", a: "-A" },
      { q: "The Nmap switch used for host discovery without port scanning is _____.", a: "-sN" },
      { q: "UDP scanning is slower because UDP is _____-oriented.", a: "connectionless" },
      { q: "Open ports represent part of a system's attack _____.", a: "surfaces" },
      { q: "Port 21 is the default port for _____.", a: "FTP" },
      { q: "Port 22 is the default port for _____.", a: "SSH" },
      { q: "Port 23 is the default port for _____, an insecure remote access protocol.", a: "Telnet" },
      { q: "Port 25 is the default port for _____ (email sending).", a: "SMTP" },
      { q: "Port 53 is the default port for _____.", a: "DNS" },
      { q: "Port 80 is the default port for _____ (unencrypted web traffic).", a: "HTTP" },
      { q: "Port 443 is the default port for _____ (encrypted web traffic).", a: "HTTPS" },
      { q: "Port 445 is the default port for _____, used for Windows file sharing.", a: "SMB" },
      { q: "Port 3389 is the default port for _____ (Remote Desktop Protocol).", a: "RDP" },
      { q: "The TCP three-way handshake consists of: SYN → _____ → ACK.", a: "SYN-ACK" },
      { q: "An Nmap _____ scan (also called half-open) sends a SYN but doesn't complete the handshake, making it stealthier.", a: "SYN" },
      { q: "The Nmap flag for a SYN (stealth) scan is _____.", a: "-sS" },
      { q: "The Nmap flag for a full TCP connect scan is _____.", a: "-sT" },
      { q: "The Nmap flag for a UDP scan is _____.", a: "-sU" },
      { q: "Ports 1024–49151 are called _____ ports.", a: "registered" },
      { q: "A _____ scan sends packets with no flags set to try to evade firewalls.", a: "null" },
      { q: "A port that responds to a SYN with SYN-ACK is considered _____.", a: "open" },
      { q: "A port that responds with RST (reset) is considered _____.", a: "closed" },
      { q: "A port that gives no response or an ICMP unreachable message is considered _____.", a: "filtered" },
      { q: "The _____ protocol operates at Layer 4 (Transport) and provides reliable, connection-oriented communication.", a: "TCP" },
      { q: "The _____ protocol operates at Layer 4 but is connectionless and faster, with no guaranteed delivery.", a: "UDP" },
    ],
  },
];

const allQuestions = sections.flatMap((s, si) =>
  s.questions.map((q, qi) => ({ ...q, section: s.title, icon: s.icon, id: `${si}-${qi}` }))
);

function normalize(s) {
  return s.toLowerCase().replace(/[^a-z0-9 ]/g, "").replace(/\s+/g, " ").trim();
}

function checkAnswer(input, answer) {
  const ni = normalize(input);
  const na = normalize(answer);
  if (!ni) return false;
  if (ni === na) return true;
  if (na.includes(ni) && ni.length > 1) return true;
  if (ni.includes(na)) return true;
  const words = na.split(" ").filter(w => w.length > 2);
  if (words.length > 1 && words.every(w => ni.includes(w))) return true;
  return false;
}

const StudyGuide = ({ filterSec, setFilterSec }) => {
  const filtered = filterSec === "all" ? sections : sections.filter(s => s.title === filterSec);
  let num = 0;
  if (filterSec !== "all") {
    for (const s of sections) {
      if (s.title === filterSec) break;
      num += s.questions.length;
    }
  }
  return (
    <div style={{ display: "flex", flexDirection: "column", gap: 16 }}>
      <select value={filterSec} onChange={e => setFilterSec(e.target.value)} style={{ padding: "8px 12px", borderRadius: 8, border: "1px solid #cbd5e1", fontSize: 14, background: "#fff" }}>
        <option value="all">All Sections ({allQuestions.length} questions)</option>
        {sections.map((s, i) => <option key={i} value={s.title}>{s.icon} {s.title} ({s.questions.length})</option>)}
      </select>
      {filtered.map((s, i) => {
        const base = filterSec === "all" ? sections.slice(0, sections.indexOf(s)).reduce((a, c) => a + c.questions.length, 0) : num;
        return (
          <div key={i} style={{ background: "#f8fafc", borderRadius: 12, padding: 18, border: "1px solid #e2e8f0" }}>
            <h3 style={{ margin: "0 0 12px", fontSize: 16, color: "#1e293b" }}>{s.icon} {s.title} <span style={{ fontSize: 13, color: "#94a3b8", fontWeight: 400 }}>({s.questions.length})</span></h3>
            <div style={{ display: "flex", flexDirection: "column", gap: 7 }}>
              {s.questions.map((q, j) => (
                <div key={j} style={{ display: "flex", gap: 8, fontSize: 13.5, lineHeight: 1.5 }}>
                  <span style={{ color: "#94a3b8", minWidth: 26, textAlign: "right" }}>{base + j + 1}.</span>
                  <span style={{ color: "#334155" }}>
                    {q.q.split("_____").map((part, pi, arr) => (
                      <span key={pi}>
                        {part}
                        {pi < arr.length - 1 && (
                          <span style={{ fontWeight: 700, color: "#2563eb", background: "#eff6ff", padding: "1px 5px", borderRadius: 4 }}>{q.a}</span>
                        )}
                      </span>
                    ))}
                  </span>
                </div>
              ))}
            </div>
          </div>
        );
      })}
    </div>
  );
};

const Quiz = () => {
  const [pool, setPool] = useState([]);
  const [current, setCurrent] = useState(0);
  const [input, setInput] = useState("");
  const [feedback, setFeedback] = useState(null);
  const [results, setResults] = useState([]);
  const [done, setDone] = useState(false);
  const [mode, setMode] = useState(null);

  const startQuiz = useCallback((m) => {
    let qs = [...allQuestions];
    if (m !== "all") qs = allQuestions.filter(q => q.section === m);
    for (let i = qs.length - 1; i > 0; i--) {
      const j = Math.floor(Math.random() * (i + 1));
      [qs[i], qs[j]] = [qs[j], qs[i]];
    }
    setPool(qs);
    setCurrent(0);
    setInput("");
    setFeedback(null);
    setResults([]);
    setDone(false);
    setMode(m);
  }, []);

  const submit = () => {
    if (!input.trim() || feedback) return;
    const correct = checkAnswer(input, pool[current].a);
    setFeedback({ correct, answer: pool[current].a });
    setResults(r => [...r, { ...pool[current], userAnswer: input, correct }]);
  };

  const next = () => {
    if (current + 1 >= pool.length) setDone(true);
    else { setCurrent(c => c + 1); setInput(""); setFeedback(null); }
  };

  if (mode === null) {
    return (
      <div style={{ display: "flex", flexDirection: "column", gap: 8 }}>
        <p style={{ color: "#64748b", fontSize: 14, margin: "0 0 8px" }}>Choose what to quiz on:</p>
        <button onClick={() => startQuiz("all")} style={{ padding: "12px 16px", borderRadius: 10, border: "2px solid #2563eb", background: "#eff6ff", cursor: "pointer", fontWeight: 700, fontSize: 15, color: "#2563eb", textAlign: "left" }}>
          All Sections — {allQuestions.length} questions
        </button>
        {sections.map((s, i) => (
          <button key={i} onClick={() => startQuiz(s.title)} style={{ padding: "10px 14px", borderRadius: 8, border: "1px solid #e2e8f0", background: "#fff", cursor: "pointer", fontWeight: 600, fontSize: 14, color: "#334155", textAlign: "left" }}>
            {s.icon} {s.title} ({s.questions.length})
          </button>
        ))}
      </div>
    );
  }

  const score = results.filter(r => r.correct).length;
  const missed = results.filter(r => !r.correct);

  if (done) {
    const pct = Math.round((score / pool.length) * 100);
    const bySection = {};
    results.forEach(r => {
      if (!bySection[r.section]) bySection[r.section] = { total: 0, correct: 0, icon: r.icon };
      bySection[r.section].total++;
      if (r.correct) bySection[r.section].correct++;
    });
    return (
      <div style={{ textAlign: "center", padding: 16 }}>
        <div style={{ fontSize: 44, marginBottom: 6 }}>{pct >= 90 ? "🎉" : pct >= 70 ? "👍" : "📚"}</div>
        <h2 style={{ margin: "0 0 4px", color: "#1e293b" }}>{score} / {pool.length}</h2>
        <p style={{ color: "#64748b", margin: "0 0 16px", fontSize: 14 }}>{pct}% — {pct >= 90 ? "You're exam ready!" : pct >= 70 ? "Almost there, drill the misses." : "Keep at it, you'll get there."}</p>
        {Object.keys(bySection).length > 1 && (
          <div style={{ textAlign: "left", marginBottom: 16 }}>
            <h4 style={{ margin: "0 0 8px", color: "#475569", fontSize: 13 }}>Breakdown:</h4>
            {Object.entries(bySection).map(([sec, d], i) => {
              const sp = Math.round((d.correct / d.total) * 100);
              return (
                <div key={i} style={{ display: "flex", alignItems: "center", gap: 8, marginBottom: 6 }}>
                  <span style={{ fontSize: 12, color: "#64748b", minWidth: 150, whiteSpace: "nowrap", overflow: "hidden", textOverflow: "ellipsis" }}>{d.icon} {sec}</span>
                  <div style={{ flex: 1, background: "#e2e8f0", borderRadius: 99, height: 8 }}>
                    <div style={{ width: `${sp}%`, background: sp >= 90 ? "#16a34a" : sp >= 70 ? "#eab308" : "#dc2626", borderRadius: 99, height: 8, transition: "width 0.3s" }} />
                  </div>
                  <span style={{ fontSize: 12, fontWeight: 600, color: sp >= 90 ? "#16a34a" : sp >= 70 ? "#a16207" : "#dc2626", minWidth: 32 }}>{sp}%</span>
                </div>
              );
            })}
          </div>
        )}
        {missed.length > 0 && (
          <div style={{ textAlign: "left", background: "#fef2f2", borderRadius: 12, padding: 14, marginBottom: 16, maxHeight: 300, overflowY: "auto" }}>
            <h4 style={{ margin: "0 0 8px", color: "#dc2626", fontSize: 13 }}>Missed ({missed.length}):</h4>
            {missed.map((m, i) => (
              <div key={i} style={{ marginBottom: 8, fontSize: 12.5, color: "#334155", paddingBottom: 8, borderBottom: i < missed.length - 1 ? "1px solid #fecaca" : "none" }}>
                <div style={{ marginBottom: 2 }}>{m.q}</div>
                <span style={{ color: "#dc2626" }}>You: {m.userAnswer}</span>
                <span style={{ color: "#16a34a", fontWeight: 600, marginLeft: 10 }}>Answer: {m.answer}</span>
              </div>
            ))}
          </div>
        )}
        <div style={{ display: "flex", gap: 8, justifyContent: "center", flexWrap: "wrap" }}>
          <button onClick={() => setMode(null)} style={{ padding: "10px 18px", borderRadius: 8, border: "none", background: "#2563eb", color: "#fff", cursor: "pointer", fontWeight: 600, fontSize: 14 }}>New Quiz</button>
          {missed.length > 0 && (
            <button onClick={() => { const s = [...missed].sort(() => Math.random() - 0.5); setPool(s); setCurrent(0); setInput(""); setFeedback(null); setResults([]); setDone(false); }} style={{ padding: "10px 18px", borderRadius: 8, border: "1px solid #e2e8f0", background: "#fff", cursor: "pointer", fontWeight: 600, fontSize: 14, color: "#334155" }}>Retry Missed ({missed.length})</button>
          )}
        </div>
      </div>
    );
  }

  const q = pool[current];
  if (!q) return null;

  return (
    <div>
      <div style={{ display: "flex", justifyContent: "space-between", alignItems: "center", marginBottom: 12 }}>
        <span style={{ fontSize: 12, color: "#64748b" }}>{q.icon} {q.section}</span>
        <span style={{ fontSize: 12, color: "#64748b", fontWeight: 600 }}>{current + 1} / {pool.length}</span>
      </div>
      <div style={{ width: "100%", background: "#e2e8f0", borderRadius: 99, height: 5, marginBottom: 18 }}>
        <div style={{ width: `${((current + 1) / pool.length) * 100}%`, background: "#2563eb", borderRadius: 99, height: 5, transition: "width 0.3s" }} />
      </div>
      <p style={{ fontSize: 15, color: "#1e293b", lineHeight: 1.6, margin: "0 0 14px" }}>{q.q}</p>
      <div style={{ display: "flex", gap: 8, marginBottom: 10 }}>
        <input value={input} onChange={e => setInput(e.target.value)} onKeyDown={e => { if (e.key === "Enter") { feedback ? next() : submit(); } }} placeholder="Type your answer..." disabled={!!feedback} autoFocus style={{ flex: 1, padding: "9px 12px", borderRadius: 8, border: "1px solid #cbd5e1", fontSize: 14, outline: "none", background: feedback ? "#f8fafc" : "#fff" }} />
        {!feedback ? (
          <button onClick={submit} disabled={!input.trim()} style={{ padding: "9px 18px", borderRadius: 8, border: "none", background: input.trim() ? "#2563eb" : "#cbd5e1", color: "#fff", cursor: input.trim() ? "pointer" : "default", fontWeight: 600, fontSize: 14 }}>Check</button>
        ) : (
          <button onClick={next} style={{ padding: "9px 18px", borderRadius: 8, border: "none", background: "#2563eb", color: "#fff", cursor: "pointer", fontWeight: 600, fontSize: 14 }}>{current + 1 >= pool.length ? "Finish" : "Next"}</button>
        )}
      </div>
      {feedback && (
        <div style={{ padding: 12, borderRadius: 10, background: feedback.correct ? "#f0fdf4" : "#fef2f2", border: `1px solid ${feedback.correct ? "#bbf7d0" : "#fecaca"}` }}>
          <span style={{ fontWeight: 700, color: feedback.correct ? "#16a34a" : "#dc2626" }}>
            {feedback.correct ? "✓ Correct!" : "✗ Not quite."}
          </span>
          {!feedback.correct && <span style={{ color: "#334155", marginLeft: 8 }}>Answer: <strong>{feedback.answer}</strong></span>}
        </div>
      )}
      <button onClick={() => setMode(null)} style={{ marginTop: 14, padding: "6px 12px", borderRadius: 6, border: "1px solid #e2e8f0", background: "#fff", cursor: "pointer", fontSize: 12, color: "#94a3b8" }}>← Back to section picker</button>
    </div>
  );
};

export default function App() {
  const [tab, setTab] = useState("quiz");
  const [filterSec, setFilterSec] = useState("all");

  return (
    <div style={{ fontFamily: "-apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif", maxWidth: 640, margin: "0 auto", padding: 16 }}>
      <div style={{ textAlign: "center", marginBottom: 16 }}>
        <h1 style={{ fontSize: 20, margin: "0 0 3px", color: "#1e293b" }}>INFSCI 1087 — Midterm Prep</h1>
        <p style={{ color: "#64748b", margin: 0, fontSize: 13 }}>Ethical Hacking • {allQuestions.length} questions • {sections.length} sections</p>
      </div>
      <div style={{ display: "flex", gap: 4, marginBottom: 20, background: "#f1f5f9", borderRadius: 10, padding: 4 }}>
        {[["quiz", "🧠 Quiz Me"], ["guide", "📖 Study Guide"]].map(([key, label]) => (
          <button key={key} onClick={() => setTab(key)} style={{ flex: 1, padding: "9px 0", borderRadius: 8, border: "none", background: tab === key ? "#fff" : "transparent", color: tab === key ? "#1e293b" : "#64748b", fontWeight: 600, cursor: "pointer", fontSize: 14, boxShadow: tab === key ? "0 1px 3px rgba(0,0,0,0.1)" : "none" }}>{label}</button>
        ))}
      </div>
      {tab === "quiz" ? <Quiz /> : <StudyGuide filterSec={filterSec} setFilterSec={setFilterSec} />}
    </div>
  );
}
