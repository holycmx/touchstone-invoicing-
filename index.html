
import { useState, useEffect, useRef, useCallback } from "react";

const FONTS_URL = "https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,500;0,600;1,300;1,400&family=Jost:wght@300;400;500;600&display=swap";

const SERVICE_TEMPLATES = {
  "Residential – Weekly": [
    { desc: "Studio / 1 Bed – Weekly Clean", qty: 1, price: 90 },
  ],
  "Residential – Weekly 2 Bed": [
    { desc: "2 Bed – Weekly Clean", qty: 1, price: 120 },
  ],
  "Residential – Weekly 3 Bed": [
    { desc: "3 Bed – Weekly Clean", qty: 1, price: 150 },
  ],
  "Residential – Weekly 4 Bed": [
    { desc: "4 Bed – Weekly Clean", qty: 1, price: 180 },
  ],
  "End of Tenancy – 1 Bed": [
    { desc: "End of Tenancy Clean – 1 Bed Flat", qty: 1, price: 200 },
  ],
  "End of Tenancy – 2 Bed": [
    { desc: "End of Tenancy Clean – 2 Bed Flat", qty: 1, price: 260 },
  ],
  "End of Tenancy – 3 Bed": [
    { desc: "End of Tenancy Clean – 3 Bed House", qty: 1, price: 320 },
  ],
  "Airbnb – Studio/1 Bed": [
    { desc: "Airbnb Turnaround Clean – Studio / 1 Bed", qty: 1, price: 105 },
  ],
  "Airbnb – 2 Bed": [
    { desc: "Airbnb Turnaround Clean – 2 Bed", qty: 1, price: 138 },
  ],
  "Airbnb – 3 Bed": [
    { desc: "Airbnb Turnaround Clean – 3 Bed", qty: 1, price: 168 },
  ],
  "Commercial – Small Office": [
    { desc: "Commercial Clean – Small Office (up to 500 sq ft)", qty: 1, price: 100 },
  ],
  "Commercial – Medium Office": [
    { desc: "Commercial Clean – Medium Office (500–1,500 sq ft)", qty: 1, price: 160 },
  ],
  "Commercial – Large Office": [
    { desc: "Commercial Clean – Large Office (1,500–3,000 sq ft)", qty: 1, price: 275 },
  ],
  "Commercial – Salon/Barbershop": [
    { desc: "Commercial Clean – Salon / Barbershop", qty: 1, price: 80 },
  ],
  "Commercial – Café/Restaurant": [
    { desc: "Commercial Clean – Café / Restaurant", qty: 1, price: 105 },
  ],
  "Commercial – Retail Unit": [
    { desc: "Commercial Clean – Retail Unit", qty: 1, price: 80 },
  ],
  "Commercial – Co-working Space": [
    { desc: "Commercial Clean – Co-working Space", qty: 1, price: 225 },
  ],
};

const NOTES_SNIPPETS = [
  "Payment is due within 14 days of the invoice date. Please use the invoice number as your payment reference.",
  "50% deposit required at booking. Remaining balance due on completion.",
  "All supplies included. No hidden charges.",
  "Thank you for choosing Touchstone Cleaners. We appreciate your business.",
  "Short notice and weekend bookings welcome. Please contact us for availability.",
  "VAT is not currently charged. Touchstone Cleaners is not VAT registered.",
];

const CURRENCIES = [
  { code: "GBP", symbol: "£", label: "GBP – British Pound" },
  { code: "USD", symbol: "$", label: "USD – US Dollar" },
  { code: "EUR", symbol: "€", label: "EUR – Euro" },
  { code: "AUD", symbol: "A$", label: "AUD – Australian Dollar" },
];

const PAYMENT_TERMS = [
  { label: "7 days", days: 7 },
  { label: "14 days", days: 14 },
  { label: "30 days", days: 30 },
  { label: "End of month", days: null, eom: true },
];

function toInputDate(d) {
  return d.toISOString().split("T")[0];
}
function formatDate(str) {
  if (!str) return "—";
  const d = new Date(str + "T12:00:00");
  return d.toLocaleDateString("en-GB", { day: "numeric", month: "long", year: "numeric" });
}
function fmt(n, symbol) {
  return (symbol || "£") + parseFloat(n || 0).toFixed(2);
}
function escHtml(s) {
  return String(s || "").replace(/&/g, "&amp;").replace(/</g, "&lt;").replace(/>/g, "&gt;");
}
function nl2br(str) {
  return (str || "").replace(/\n/g, "<br>");
}
function nextInvoiceNumber(cur) {
  const match = cur.match(/(\D+)(\d+)$/);
  if (match) return match[1] + String(parseInt(match[2]) + 1).padStart(3, "0");
  return cur + "-002";
}

export default function Home() {
  const today = new Date();
  const due14 = new Date(today); due14.setDate(due14.getDate() + 14);

  const defaultState = () => ({
    invNumber: "INV-001",
    invDate: toInputDate(today),
    invDue: toInputDate(due14),
    invRef: "",
    status: "pending",
    clientName: "",
    clientAddress: "",
    clientEmail: "",
    bizName: "Touchstone Cleaners",
    bizAddress: "Unit A402, 4–6 Greatorex Street\nLondon, E1",
    bizEmail: "hello@touchstonecleaners.co.uk",
    bizWebsite: "touchstonecleaners.co.uk",
    bankName: "The Revenue Rooms Ltd",
    bankSort: "04-06-05",
    bankAcc: "25797352",
    bizReg: "The Revenue Rooms Ltd t/a Touchstone Cleaners\nRegistered in England & Wales · Co. No. 16180320",
    notes: "Thank you for choosing Touchstone Cleaners. Payment is due within 14 days of the invoice date. Please use the invoice number as your payment reference.",
    vatRate: 0,
    discount: 0,
    depositPaid: 0,
    currency: "GBP",
    lineItems: [{ id: "line-1", desc: "End of Tenancy Clean – 2 Bed Flat", qty: 1, price: 260 }],
  });

  const [state, setState] = useState(defaultState);
  const [lineCounter, setLineCounter] = useState(2);
  const [showDraftBanner, setShowDraftBanner] = useState(false);
  const [showShortcuts, setShowShortcuts] = useState(false);
  const [showTemplates, setShowTemplates] = useState(false);
  const [showSnippets, setShowSnippets] = useState(false);
  const [showExportMenu, setShowExportMenu] = useState(false);
  const [showValidation, setShowValidation] = useState(false);
  const [validationErrors, setValidationErrors] = useState([]);
  const [copySuccess, setCopySuccess] = useState(false);
  const [pdfLoading, setPdfLoading] = useState(false);
  const [activeTab, setActiveTab] = useState("details");
  const [undoStack, setUndoStack] = useState([]);
  const [savedTemplates, setSavedTemplates] = useState({});
  const [templateNameInput, setTemplateNameInput] = useState("");
  const [showSaveTemplate, setShowSaveTemplate] = useState(false);
  const autoSaveTimer = useRef(null);
  const previewRef = useRef(null);

  const currencySymbol = CURRENCIES.find(c => c.code === state.currency)?.symbol || "£";

  // Load from localStorage on mount
  useEffect(() => {
    const draft = localStorage.getItem("tc_invoice_draft");
    const savedTpls = localStorage.getItem("tc_saved_templates");
    if (savedTpls) {
      try { setSavedTemplates(JSON.parse(savedTpls)); } catch (e) {}
    }
    if (draft) {
      try {
        const parsed = JSON.parse(draft);
        if (parsed && parsed.invNumber) {
          setShowDraftBanner(true);
        }
      } catch (e) {}
    }
  }, []);

  // Auto-save every 30s
  useEffect(() => {
    if (autoSaveTimer.current) clearInterval(autoSaveTimer.current);
    autoSaveTimer.current = setInterval(() => {
      localStorage.setItem("tc_invoice_draft", JSON.stringify(state));
    }, 30000);
    return () => clearInterval(autoSaveTimer.current);
  }, [state]);

  const restoreDraft = () => {
    const draft = localStorage.getItem("tc_invoice_draft");
    if (draft) {
      try {
        const parsed = JSON.parse(draft);
        setState(parsed);
        const maxId = (parsed.lineItems || []).reduce((m, l) => {
          const n = parseInt(l.id.replace("line-", "")) || 0;
          return Math.max(m, n);
        }, 0);
        setLineCounter(maxId + 1);
      } catch (e) {}
    }
    setShowDraftBanner(false);
  };

  const set = (field, value) => {
    setUndoStack(prev => [...prev.slice(-19), state]);
    setState(prev => ({ ...prev, [field]: value }));
  };

  const undo = useCallback(() => {
    if (undoStack.length === 0) return;
    const prev = undoStack[undoStack.length - 1];
    setUndoStack(s => s.slice(0, -1));
    setState(prev);
  }, [undoStack, state]);

  // Keyboard shortcuts
  useEffect(() => {
    const handler = (e) => {
      if ((e.ctrlKey || e.metaKey) && e.key === "n") { e.preventDefault(); handleNew(); }
      if ((e.ctrlKey || e.metaKey) && e.key === "Enter") { e.preventDefault(); handleDownloadPDF(); }
      if ((e.ctrlKey || e.metaKey) && e.key === "z") { e.preventDefault(); undo(); }
      if (e.key === "?" && !e.target.matches("input,textarea")) { setShowShortcuts(true); }
    };
    window.addEventListener("keydown", handler);
    return () => window.removeEventListener("keydown", handler);
  }, [undo]);

  const addLine = (desc = "", qty = 1, price = 0) => {
    const id = `line-${lineCounter}`;
    setLineCounter(c => c + 1);
    setState(prev => ({ ...prev, lineItems: [...prev.lineItems, { id, desc, qty, price }] }));
  };

  const removeLine = (id) => {
    setUndoStack(prev => [...prev.slice(-19), state]);
    setState(prev => ({ ...prev, lineItems: prev.lineItems.filter(l => l.id !== id) }));
  };

  const updateLine = (id, field, val) => {
    setState(prev => ({
      ...prev,
      lineItems: prev.lineItems.map(l => {
        if (l.id !== id) return l;
        if (field === "qty") return { ...l, qty: parseFloat(val) || 1 };
        if (field === "price") return { ...l, price: parseFloat(val) || 0 };
        return { ...l, [field]: val };
      }),
    }));
  };

  const subtotal = state.lineItems.reduce((s, l) => s + (parseFloat(l.qty) || 0) * (parseFloat(l.price) || 0), 0);
  const disc = parseFloat(state.discount) || 0;
  const vatRate = parseFloat(state.vatRate) || 0;
  const afterDisc = subtotal - disc;
  const vat = afterDisc * (vatRate / 100);
  const deposit = parseFloat(state.depositPaid) || 0;
  const grand = afterDisc + vat;
  const balanceDue = grand - deposit;

  const setDeposit = (pct) => set("depositPaid", ((subtotal * pct) / 100).toFixed(2));

  const setPaymentTerms = (termObj) => {
    const base = new Date(state.invDate + "T12:00:00");
    if (termObj.eom) {
      base.setMonth(base.getMonth() + 1, 0);
    } else {
      base.setDate(base.getDate() + termObj.days);
    }
    set("invDue", toInputDate(base));
  };

  const handleNew = () => {
    if (!window.confirm("Start a new invoice? This will clear the current one.")) return;
    const newState = defaultState();
    newState.invNumber = nextInvoiceNumber(state.invNumber);
    setState(newState);
    setLineCounter(2);
    setUndoStack([]);
  };

  const validate = () => {
    const errors = [];
    if (!state.clientName.trim()) errors.push("Client name is required");
    if (state.lineItems.length === 0) errors.push("At least one service line is required");
    if (state.lineItems.some(l => !l.desc.trim())) errors.push("All service lines need a description");
    if (disc < 0 || deposit < 0 || vatRate < 0) errors.push("Negative values are not allowed");
    return errors;
  };

  const loadTemplate = (name) => {
    const lines = SERVICE_TEMPLATES[name] || savedTemplates[name];
    if (!lines) return;
    setUndoStack(prev => [...prev.slice(-19), state]);
    const newLines = lines.map((l, i) => ({ ...l, id: `line-${lineCounter + i}` }));
    setLineCounter(c => c + lines.length);
    setState(prev => ({ ...prev, lineItems: [...prev.lineItems, ...newLines] }));
    setShowTemplates(false);
  };

  const saveCurrentAsTemplate = () => {
    if (!templateNameInput.trim()) return;
    const tpl = state.lineItems.map(l => ({ desc: l.desc, qty: l.qty, price: l.price }));
    const updated = { ...savedTemplates, [templateNameInput.trim()]: tpl };
    setSavedTemplates(updated);
    localStorage.setItem("tc_saved_templates", JSON.stringify(updated));
    setTemplateNameInput("");
    setShowSaveTemplate(false);
  };

  const copySummary = () => {
    const text = `Invoice: ${state.invNumber}\nClient: ${state.clientName || "—"}\nDate: ${formatDate(state.invDate)}\nDue: ${formatDate(state.invDue)}\nTotal: ${fmt(balanceDue, currencySymbol)}\nStatus: ${state.status.toUpperCase()}`;
    navigator.clipboard.writeText(text).then(() => {
      setCopySuccess(true);
      setTimeout(() => setCopySuccess(false), 2500);
    });
  };

  const exportCSV = () => {
    const rows = [["Description", "Qty", "Unit Price", "Line Total"]];
    state.lineItems.forEach(l => rows.push([l.desc, l.qty, l.price, (l.qty * l.price).toFixed(2)]));
    rows.push(["", "", "Subtotal", subtotal.toFixed(2)]);
    if (disc > 0) rows.push(["", "", "Discount", (-disc).toFixed(2)]);
    if (vatRate > 0) rows.push(["", "", `VAT (${vatRate}%)`, vat.toFixed(2)]);
    if (deposit > 0) rows.push(["", "", "Deposit Paid", (-deposit).toFixed(2)]);
    rows.push(["", "", "BALANCE DUE", balanceDue.toFixed(2)]);
    const csv = rows.map(r => r.map(c => `"${c}"`).join(",")).join("\n");
    const blob = new Blob([csv], { type: "text/csv" });
    const a = document.createElement("a"); a.href = URL.createObjectURL(blob);
    a.download = `Touchstone-${state.invNumber}.csv`; a.click();
    setShowExportMenu(false);
  };

  const exportJSON = () => {
    const data = { ...state, totals: { subtotal, discount: disc, vat, depositPaid: deposit, grandTotal: grand, balanceDue } };
    const blob = new Blob([JSON.stringify(data, null, 2)], { type: "application/json" });
    const a = document.createElement("a"); a.href = URL.createObjectURL(blob);
    a.download = `Touchstone-${state.invNumber}.json`; a.click();
    setShowExportMenu(false);
  };

  const printInvoice = () => {
    const w = window.open("", "_blank");
    const el = previewRef.current;
    if (!el || !w) return;
    w.document.write(`<!DOCTYPE html><html><head><meta charset="UTF-8"><link href="${FONTS_URL}" rel="stylesheet"><style>body{margin:0;padding:0;background:white;}@media print{body{margin:0;}}</style></head><body>${el.outerHTML}<script>window.onload=function(){window.print();}<\/script></body></html>`);
    w.document.close();
  };

  const handleDownloadPDF = async () => {
    const errors = validate();
    if (errors.length > 0) {
      setValidationErrors(errors);
      setShowValidation(true);
      return;
    }
    setPdfLoading(true);
    try {
      // Dynamically load libs if not present
      if (!window.jspdf) {
        await new Promise((res, rej) => {
          const s = document.createElement("script");
          s.src = "https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js";
          s.onload = res; s.onerror = rej;
          document.head.appendChild(s);
        });
      }
      if (!window.html2canvas) {
        await new Promise((res, rej) => {
          const s = document.createElement("script");
          s.src = "https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js";
          s.onload = res; s.onerror = rej;
          document.head.appendChild(s);
        });
      }
      const el = previewRef.current;
      const origStyle = el.style.cssText;
      const MIN_HEIGHT = 1123;
      if (el.offsetHeight < MIN_HEIGHT) { el.style.height = MIN_HEIGHT + "px"; el.style.minHeight = "0"; }
      const canvas = await window.html2canvas(el, { scale: 2, useCORS: true, backgroundColor: "#FDFCFA", logging: false, windowWidth: 794, width: 794 });
      el.style.cssText = origStyle;
      const { jsPDF } = window.jspdf;
      const pdf = new jsPDF({ orientation: "portrait", unit: "mm", format: "a4" });
      const pdfW = pdf.internal.pageSize.getWidth();
      const pdfH = pdf.internal.pageSize.getHeight();
      const ratio = pdfW / canvas.width;
      const scaledH = canvas.height * ratio;
      if (scaledH <= pdfH) {
        pdf.addImage(canvas.toDataURL("image/png"), "PNG", 0, 0, pdfW, scaledH);
      } else {
        let y = 0;
        const pageHPx = canvas.height * (pdfH / scaledH);
        while (y < canvas.height) {
          if (y > 0) pdf.addPage();
          const sliceCanvas = document.createElement("canvas");
          sliceCanvas.width = canvas.width;
          sliceCanvas.height = Math.min(pageHPx, canvas.height - y);
          const ctx = sliceCanvas.getContext("2d");
          ctx.fillStyle = "#FDFCFA"; ctx.fillRect(0, 0, sliceCanvas.width, sliceCanvas.height);
          ctx.drawImage(canvas, 0, -y);
          pdf.addImage(sliceCanvas.toDataURL("image/png"), "PNG", 0, 0, pdfW, sliceCanvas.height * ratio);
          y += pageHPx;
        }
      }
      pdf.save(`Touchstone-${state.invNumber}.pdf`);
    } catch (e) { alert("PDF generation failed. Please try again."); }
    setPdfLoading(false);
  };

  const styles = `
    @import url('${FONTS_URL}');
    *,*::before,*::after{box-sizing:border-box;margin:0;padding:0;}
    :root{--cream:#F8F6F1;--warm-white:#FDFCFA;--dark:#1A1A1A;--mid:#555555;--light:#999999;--rule:#E0DDD7;--accent:#1A1A2E;--gold:#C9A84C;--gold-light:#E8D48A;--serif:'Cormorant Garamond',Georgia,serif;--sans:'Jost',sans-serif;}
    body{font-family:var(--sans);background:#13131F;color:var(--dark);min-height:100vh;font-weight:300;}
    .app-header{background:var(--accent);border-bottom:1px solid rgba(201,168,76,0.3);padding:14px 32px;display:flex;align-items:center;justify-content:space-between;position:sticky;top:0;z-index:100;}
    .app-header-logo{font-family:var(--serif);font-size:18px;letter-spacing:4px;color:white;font-weight:400;}
    .app-header-sub{font-family:var(--sans);font-size:9px;letter-spacing:4px;color:var(--gold);display:block;margin-top:2px;}
    .app-header-actions{display:flex;gap:8px;align-items:center;flex-wrap:wrap;}
    .btn-gold{background:var(--gold);color:var(--accent);border:none;padding:10px 20px;font-family:var(--sans);font-size:10px;font-weight:600;letter-spacing:2px;text-transform:uppercase;cursor:pointer;transition:all 0.2s;}
    .btn-gold:hover{background:var(--gold-light);}
    .btn-ghost{background:rgba(255,255,255,0.08);color:rgba(255,255,255,0.8);border:0.5px solid rgba(255,255,255,0.15);padding:10px 16px;font-family:var(--sans);font-size:10px;letter-spacing:1.5px;text-transform:uppercase;cursor:pointer;transition:all 0.2s;}
    .btn-ghost:hover{background:rgba(255,255,255,0.13);}
    .app-layout{display:grid;grid-template-columns:370px 1fr;min-height:calc(100vh - 65px);}
    .sidebar{background:#1A1A2E;border-right:1px solid rgba(201,168,76,0.12);overflow-y:auto;max-height:calc(100vh - 65px);position:sticky;top:65px;}
    .sidebar-tabs{display:flex;border-bottom:1px solid rgba(201,168,76,0.15);}
    .sidebar-tab{flex:1;padding:12px 6px;font-family:var(--sans);font-size:9px;letter-spacing:2px;text-transform:uppercase;color:rgba(255,255,255,0.35);background:none;border:none;cursor:pointer;transition:all 0.2s;border-bottom:2px solid transparent;margin-bottom:-1px;}
    .sidebar-tab.active{color:var(--gold);border-bottom-color:var(--gold);}
    .sidebar-inner{padding:24px 22px;}
    .sidebar-section{margin-bottom:28px;border-bottom:0.5px solid rgba(255,255,255,0.06);padding-bottom:28px;}
    .sidebar-section:last-child{border-bottom:none;margin-bottom:0;}
    .sidebar-label{font-family:var(--sans);font-size:9px;letter-spacing:3px;text-transform:uppercase;color:var(--gold);margin-bottom:14px;display:flex;align-items:center;gap:8px;}
    .sidebar-label::after{content:'';flex:1;height:0.5px;background:rgba(201,168,76,0.25);}
    .form-field{margin-bottom:12px;}
    .form-field label{display:block;font-size:9px;letter-spacing:2px;text-transform:uppercase;color:rgba(255,255,255,0.3);margin-bottom:5px;}
    .form-field input,.form-field textarea,.form-field select{width:100%;background:rgba(255,255,255,0.05);border:0.5px solid rgba(255,255,255,0.1);color:rgba(255,255,255,0.85);padding:9px 11px;font-family:var(--sans);font-size:13px;font-weight:300;outline:none;transition:border-color 0.2s;appearance:none;-webkit-appearance:none;}
    .form-field input:focus,.form-field textarea:focus,.form-field select:focus{border-color:rgba(201,168,76,0.5);}
    .form-field input::placeholder,.form-field textarea::placeholder{color:rgba(255,255,255,0.18);}
    .form-field textarea{resize:vertical;min-height:58px;}
    .form-field select option{background:#1A1A2E;color:white;}
    .form-row{display:grid;grid-template-columns:1fr 1fr;gap:10px;}
    .form-row-3{display:grid;grid-template-columns:1fr 1fr 1fr;gap:8px;}
    .status-options{display:flex;gap:6px;}
    .status-opt{flex:1;padding:8px 4px;border:0.5px solid rgba(255,255,255,0.1);background:none;color:rgba(255,255,255,0.4);font-family:var(--sans);font-size:9px;letter-spacing:1px;text-transform:uppercase;cursor:pointer;transition:all 0.2s;text-align:center;}
    .status-opt.active-paid{background:rgba(34,139,34,0.15);border-color:#4caf50;color:#81c784;}
    .status-opt.active-pending{background:rgba(201,168,76,0.15);border-color:var(--gold);color:var(--gold);}
    .status-opt.active-overdue{background:rgba(198,40,40,0.15);border-color:#ef5350;color:#ef9a9a;}
    .line-items{display:flex;flex-direction:column;gap:8px;}
    .line-item{background:rgba(255,255,255,0.04);border:0.5px solid rgba(255,255,255,0.08);padding:12px;position:relative;}
    .line-item-grid{display:grid;grid-template-columns:1fr 64px 64px;gap:6px;align-items:end;}
    .line-item-remove{position:absolute;top:7px;right:7px;background:none;border:none;color:rgba(255,255,255,0.25);cursor:pointer;font-size:15px;line-height:1;padding:2px;transition:color 0.2s;}
    .line-item-remove:hover{color:#c62828;}
    .btn-add-line{width:100%;background:none;border:0.5px dashed rgba(201,168,76,0.3);color:var(--gold);padding:9px;font-family:var(--sans);font-size:9px;letter-spacing:2px;text-transform:uppercase;cursor:pointer;transition:all 0.2s;margin-top:8px;}
    .btn-add-line:hover{background:rgba(201,168,76,0.05);border-color:var(--gold);}
    .deposit-btns{display:flex;gap:6px;margin-top:6px;}
    .deposit-btn{flex:1;background:rgba(201,168,76,0.1);border:0.5px solid rgba(201,168,76,0.3);color:var(--gold);padding:7px 4px;font-family:var(--sans);font-size:9px;letter-spacing:1px;cursor:pointer;transition:all 0.2s;text-align:center;}
    .deposit-btn:hover{background:rgba(201,168,76,0.2);}
    .terms-btns{display:flex;gap:5px;flex-wrap:wrap;margin-top:6px;}
    .terms-btn{background:rgba(255,255,255,0.06);border:0.5px solid rgba(255,255,255,0.12);color:rgba(255,255,255,0.6);padding:6px 8px;font-family:var(--sans);font-size:9px;letter-spacing:1px;cursor:pointer;transition:all 0.2s;}
    .terms-btn:hover{background:rgba(255,255,255,0.12);color:white;}
    .preview-area{background:#0D0D1A;padding:36px 32px;display:flex;flex-direction:column;align-items:center;overflow-y:auto;}
    .preview-label{font-size:9px;letter-spacing:3px;text-transform:uppercase;color:rgba(255,255,255,0.18);margin-bottom:20px;align-self:flex-start;}
    #invoice-preview{width:794px;min-height:1123px;background:var(--warm-white);box-shadow:0 24px 60px rgba(0,0,0,0.7);position:relative;overflow:hidden;}
    .inv-header{background:var(--accent);padding:44px 52px 36px;display:flex;justify-content:space-between;align-items:flex-start;position:relative;}
    .inv-header::after{content:'';position:absolute;bottom:0;left:0;right:0;height:3px;background:linear-gradient(90deg,var(--gold),transparent);}
    .inv-logo-text{font-family:var(--serif);font-size:28px;font-weight:400;letter-spacing:6px;color:white;line-height:1;}
    .inv-logo-sub{font-family:var(--sans);font-size:9px;letter-spacing:5px;color:rgba(201,168,76,0.8);display:block;margin-top:4px;}
    .inv-header-right{text-align:right;}
    .inv-number{font-family:var(--serif);font-size:36px;font-weight:300;color:white;line-height:1;}
    .inv-number-label{font-family:var(--sans);font-size:9px;letter-spacing:3px;text-transform:uppercase;color:rgba(255,255,255,0.35);margin-bottom:6px;}
    .inv-status-badge{display:inline-block;padding:4px 14px;font-family:var(--sans);font-size:9px;letter-spacing:2px;text-transform:uppercase;margin-top:10px;}
    .inv-status-badge.paid{background:rgba(76,175,80,0.2);color:#81c784;border:0.5px solid #4caf50;}
    .inv-status-badge.pending{background:rgba(201,168,76,0.2);color:var(--gold);border:0.5px solid var(--gold);}
    .inv-status-badge.overdue{background:rgba(198,40,40,0.2);color:#ef9a9a;border:0.5px solid #ef5350;}
    .inv-body{padding:36px 52px;}
    .inv-meta{display:grid;grid-template-columns:1fr 1fr 1fr;gap:24px;margin-bottom:36px;padding-bottom:36px;border-bottom:0.5px solid var(--rule);}
    .inv-meta-label{font-family:var(--sans);font-size:8px;letter-spacing:3px;text-transform:uppercase;color:var(--light);margin-bottom:8px;}
    .inv-meta-value{font-family:var(--sans);font-size:13px;font-weight:400;color:var(--dark);line-height:1.6;}
    .inv-addresses{display:grid;grid-template-columns:1fr 1fr;gap:40px;margin-bottom:36px;padding-bottom:36px;border-bottom:0.5px solid var(--rule);}
    .inv-address-label{font-family:var(--sans);font-size:8px;letter-spacing:3px;text-transform:uppercase;color:var(--light);margin-bottom:10px;}
    .inv-address-name{font-family:var(--serif);font-size:20px;font-weight:400;color:var(--dark);margin-bottom:6px;}
    .inv-address-text{font-family:var(--sans);font-size:13px;color:var(--mid);line-height:1.7;font-weight:300;}
    .inv-table{width:100%;border-collapse:collapse;margin-bottom:28px;}
    .inv-table thead tr{border-bottom:0.5px solid var(--rule);}
    .inv-table th{font-family:var(--sans);font-size:8px;letter-spacing:3px;text-transform:uppercase;color:var(--light);padding:10px 0;text-align:left;font-weight:400;}
    .inv-table th:last-child,.inv-table th:nth-child(3){text-align:right;}
    .inv-table th:nth-child(2){text-align:center;}
    .inv-table tbody tr{border-bottom:0.5px solid rgba(224,221,215,0.5);}
    .inv-table td{padding:14px 0;font-family:var(--sans);font-size:13px;color:var(--mid);font-weight:300;}
    .inv-table td:first-child{font-family:var(--serif);font-size:16px;color:var(--dark);font-weight:400;padding-right:16px;}
    .inv-table td:nth-child(2){text-align:center;}
    .inv-table td:nth-child(3),.inv-table td:last-child{text-align:right;}
    .inv-table td:last-child{font-weight:400;color:var(--dark);}
    .inv-totals{display:flex;justify-content:flex-end;margin-bottom:36px;}
    .inv-totals-inner{width:280px;}
    .inv-total-row{display:flex;justify-content:space-between;align-items:center;padding:8px 0;border-bottom:0.5px solid rgba(224,221,215,0.5);}
    .inv-total-label{font-family:var(--sans);font-size:11px;letter-spacing:1px;color:var(--light);text-transform:uppercase;}
    .inv-total-value{font-family:var(--serif);font-size:16px;color:var(--mid);font-weight:400;}
    .inv-total-row.grand{border-bottom:none;border-top:1px solid var(--accent);padding-top:14px;margin-top:4px;}
    .inv-total-row.grand .inv-total-label{font-size:10px;font-weight:600;color:var(--accent);letter-spacing:2px;}
    .inv-total-row.grand .inv-total-value{font-size:28px;color:var(--accent);font-weight:600;}
    .inv-bottom{display:grid;grid-template-columns:1fr 1fr;gap:40px;padding-top:28px;border-top:0.5px solid var(--rule);}
    .inv-notes-label,.inv-bank-label{font-family:var(--sans);font-size:8px;letter-spacing:3px;text-transform:uppercase;color:var(--light);margin-bottom:10px;}
    .inv-notes-text{font-family:var(--sans);font-size:12px;color:var(--mid);line-height:1.7;font-weight:300;}
    .inv-bank-row{display:flex;justify-content:space-between;padding:6px 0;border-bottom:0.5px solid rgba(224,221,215,0.4);}
    .inv-bank-row:last-child{border-bottom:none;}
    .inv-bank-key{font-family:var(--sans);font-size:10px;letter-spacing:1px;color:var(--light);text-transform:uppercase;}
    .inv-bank-val{font-family:var(--sans);font-size:12px;color:var(--dark);font-weight:400;}
    .inv-footer{background:var(--accent);padding:18px 52px;display:flex;align-items:center;justify-content:space-between;margin-top:28px;position:relative;}
    .inv-footer::before{content:'';position:absolute;top:0;left:0;right:0;height:2px;background:linear-gradient(90deg,var(--gold),transparent);}
    .inv-footer-left{font-family:var(--sans);font-size:10px;color:rgba(255,255,255,0.35);line-height:1.6;}
    .inv-footer-right{font-family:var(--serif);font-size:13px;color:rgba(201,168,76,0.6);letter-spacing:2px;}
    .modal-overlay{position:fixed;inset:0;background:rgba(0,0,0,0.7);z-index:200;display:flex;align-items:center;justify-content:center;padding:20px;}
    .modal{background:#1A1A2E;border:0.5px solid rgba(201,168,76,0.2);padding:28px;max-width:520px;width:100%;max-height:80vh;overflow-y:auto;}
    .modal-title{font-family:var(--serif);font-size:22px;color:white;font-weight:400;margin-bottom:18px;}
    .modal-close{position:absolute;top:14px;right:14px;background:none;border:none;color:rgba(255,255,255,0.4);font-size:22px;cursor:pointer;line-height:1;}
    .modal-close:hover{color:white;}
    .shortcut-row{display:flex;justify-content:space-between;align-items:center;padding:10px 0;border-bottom:0.5px solid rgba(255,255,255,0.06);}
    .shortcut-row:last-child{border-bottom:none;}
    .shortcut-key{background:rgba(255,255,255,0.1);border:0.5px solid rgba(255,255,255,0.15);padding:4px 10px;font-family:var(--sans);font-size:11px;color:var(--gold);letter-spacing:1px;}
    .shortcut-desc{font-family:var(--sans);font-size:12px;color:rgba(255,255,255,0.6);}
    .tpl-btn{width:100%;text-align:left;background:rgba(255,255,255,0.04);border:0.5px solid rgba(255,255,255,0.08);color:rgba(255,255,255,0.75);padding:11px 14px;font-family:var(--sans);font-size:12px;cursor:pointer;transition:all 0.2s;margin-bottom:4px;display:flex;justify-content:space-between;align-items:center;}
    .tpl-btn:hover{background:rgba(201,168,76,0.1);border-color:rgba(201,168,76,0.3);color:white;}
    .tpl-price{font-size:11px;color:var(--gold);}
    .tpl-group{font-size:9px;letter-spacing:2px;text-transform:uppercase;color:rgba(201,168,76,0.6);margin:14px 0 8px;}
    .snippet-btn{width:100%;text-align:left;background:rgba(255,255,255,0.04);border:0.5px solid rgba(255,255,255,0.08);color:rgba(255,255,255,0.7);padding:10px 13px;font-family:var(--sans);font-size:12px;cursor:pointer;transition:all 0.2s;margin-bottom:4px;line-height:1.5;}
    .snippet-btn:hover{background:rgba(201,168,76,0.1);border-color:rgba(201,168,76,0.3);color:white;}
    .validation-error{background:rgba(198,40,40,0.1);border:0.5px solid #ef5350;padding:8px 12px;font-family:var(--sans);font-size:12px;color:#ef9a9a;margin-bottom:6px;}
    .banner{background:rgba(201,168,76,0.12);border-bottom:1px solid rgba(201,168,76,0.25);padding:10px 32px;display:flex;align-items:center;justify-content:space-between;gap:12px;}
    .banner-text{font-family:var(--sans);font-size:12px;color:rgba(255,255,255,0.7);}
    .banner-btns{display:flex;gap:8px;}
    .dropdown-menu{position:absolute;top:calc(100% + 4px);right:0;background:#1A1A2E;border:0.5px solid rgba(201,168,76,0.25);min-width:180px;z-index:50;}
    .dropdown-item{display:block;width:100%;text-align:left;background:none;border:none;color:rgba(255,255,255,0.75);padding:11px 16px;font-family:var(--sans);font-size:11px;letter-spacing:1px;cursor:pointer;transition:background 0.15s;}
    .dropdown-item:hover{background:rgba(201,168,76,0.1);color:white;}
    .line-total-val{opacity:0.5;cursor:default;}
    .sidebar::-webkit-scrollbar{width:3px;}
    .sidebar::-webkit-scrollbar-track{background:transparent;}
    .sidebar::-webkit-scrollbar-thumb{background:rgba(201,168,76,0.2);border-radius:2px;}
    @media(max-width:1200px){.app-layout{grid-template-columns:300px 1fr;}#invoice-preview{width:650px;transform:scale(0.88);transform-origin:top center;}}
  `;

  const tplGroups = {
    "RESIDENTIAL": ["Residential – Weekly", "Residential – Weekly 2 Bed", "Residential – Weekly 3 Bed", "Residential – Weekly 4 Bed"],
    "END OF TENANCY": ["End of Tenancy – 1 Bed", "End of Tenancy – 2 Bed", "End of Tenancy – 3 Bed"],
    "AIRBNB / SHORT LETS": ["Airbnb – Studio/1 Bed", "Airbnb – 2 Bed", "Airbnb – 3 Bed"],
    "COMMERCIAL": ["Commercial – Small Office", "Commercial – Medium Office", "Commercial – Large Office", "Commercial – Salon/Barbershop", "Commercial – Café/Restaurant", "Commercial – Retail Unit", "Commercial – Co-working Space"],
  };
  const savedTplKeys = Object.keys(savedTemplates);

  return (
    <div>
      <style>{styles}</style>

      {/* HEADER */}
      <header className="app-header">
        <div>
          <div className="app-header-logo">TOUCHSTONE</div>
          <span className="app-header-sub">INVOICE GENERATOR</span>
        </div>
        <div className="app-header-actions">
          <button className="btn-ghost" onClick={() => setShowShortcuts(true)} title="Keyboard shortcuts (?)">⌨ Keys</button>
          <button className="btn-ghost" onClick={copySummary}>{copySuccess ? "✓ Copied!" : "Copy Summary"}</button>
          <button className="btn-ghost" onClick={printInvoice}>🖨 Print</button>
          <div style={{ position: "relative" }}>
            <button className="btn-ghost" onClick={() => setShowExportMenu(v => !v)}>Export ▾</button>
            {showExportMenu && (
              <div className="dropdown-menu">
                <button className="dropdown-item" onClick={exportCSV}>Download CSV</button>
                <button className="dropdown-item" onClick={exportJSON}>Download JSON</button>
              </div>
            )}
          </div>
          <button className="btn-ghost" onClick={handleNew}>New Invoice</button>
          <button className="btn-gold" onClick={handleDownloadPDF} disabled={pdfLoading}>
            {pdfLoading ? "Generating…" : "⬇ Download PDF"}
          </button>
        </div>
      </header>

      {/* DRAFT RECOVERY BANNER */}
      {showDraftBanner && (
        <div className="banner">
          <span className="banner-text">📋 You have an unsaved draft from a previous session.</span>
          <div className="banner-btns">
            <button className="btn-ghost" style={{ padding: "7px 14px", fontSize: "10px" }} onClick={restoreDraft}>Restore Draft</button>
            <button className="btn-ghost" style={{ padding: "7px 14px", fontSize: "10px", opacity: 0.5 }} onClick={() => setShowDraftBanner(false)}>Dismiss</button>
          </div>
        </div>
      )}

      <div className="app-layout">
        {/* SIDEBAR */}
        <aside className="sidebar">
          <div className="sidebar-tabs">
            {["details", "client", "services", "settings"].map(tab => (
              <button key={tab} className={`sidebar-tab${activeTab === tab ? " active" : ""}`} onClick={() => setActiveTab(tab)}>
                {tab === "details" ? "Invoice" : tab === "client" ? "Client" : tab === "services" ? "Services" : "Business"}
              </button>
            ))}
          </div>
          <div className="sidebar-inner">

            {/* INVOICE DETAILS TAB */}
            {activeTab === "details" && (
              <>
                <div className="sidebar-section">
                  <div className="sidebar-label">Invoice Details</div>
                  <div className="form-row">
                    <div className="form-field">
                      <label>Invoice No.</label>
                      <input type="text" value={state.invNumber} onChange={e => set("invNumber", e.target.value)} />
                    </div>
                    <div className="form-field">
                      <label>Currency</label>
                      <select value={state.currency} onChange={e => set("currency", e.target.value)}>
                        {CURRENCIES.map(c => <option key={c.code} value={c.code}>{c.label}</option>)}
                      </select>
                    </div>
                  </div>
                  <div className="form-row">
                    <div className="form-field">
                      <label>Date Issued</label>
                      <input type="date" value={state.invDate} onChange={e => set("invDate", e.target.value)} />
                    </div>
                    <div className="form-field">
                      <label>Due Date</label>
                      <input type="date" value={state.invDue} onChange={e => set("invDue", e.target.value)} />
                    </div>
                  </div>
                  <div className="form-field">
                    <label>Due Date Calculator</label>
                    <div className="terms-btns">
                      {PAYMENT_TERMS.map(t => (
                        <button key={t.label} className="terms-btn" onClick={() => setPaymentTerms(t)}>{t.label}</button>
                      ))}
                    </div>
                  </div>
                  <div className="form-field">
                    <label>PO / Reference</label>
                    <input type="text" value={state.invRef} placeholder="Optional" onChange={e => set("invRef", e.target.value)} />
                  </div>
                  <div className="form-field">
                    <label>Status</label>
                    <div className="status-options">
                      {["pending", "paid", "overdue"].map(s => (
                        <button key={s} className={`status-opt${state.status === s ? " active-" + s : ""}`} onClick={() => set("status", s)}>
                          {s.charAt(0).toUpperCase() + s.slice(1)}
                        </button>
                      ))}
                    </div>
                  </div>
                </div>
                <div className="sidebar-section">
                  <div className="sidebar-label">Notes</div>
                  <div className="form-field">
                    <textarea rows={4} value={state.notes} onChange={e => set("notes", e.target.value)} />
                  </div>
                  <button className="btn-add-line" onClick={() => setShowSnippets(true)}>+ Insert Note Snippet</button>
                </div>
              </>
            )}

            {/* CLIENT TAB */}
            {activeTab === "client" && (
              <div className="sidebar-section">
                <div className="sidebar-label">Bill To (Client)</div>
                <div className="form-field">
                  <label>Client Name / Company</label>
                  <input type="text" value={state.clientName} placeholder="Jane Smith" onChange={e => set("clientName", e.target.value)} />
                </div>
                <div className="form-field">
                  <label>Address</label>
                  <textarea value={state.clientAddress} placeholder={"12 Example Street\nLondon, SE1 2AB"} rows={3} onChange={e => set("clientAddress", e.target.value)} />
                </div>
                <div className="form-field">
                  <label>Email</label>
                  <input type="email" value={state.clientEmail} placeholder="client@email.com" onChange={e => set("clientEmail", e.target.value)} />
                </div>
              </div>
            )}

            {/* SERVICES TAB */}
            {activeTab === "services" && (
              <>
                <div className="sidebar-section">
                  <div className="sidebar-label">Services</div>
                  <div className="line-items">
                    {state.lineItems.map(l => (
                      <div className="line-item" key={l.id}>
                        <button className="line-item-remove" onClick={() => removeLine(l.id)} title="Remove">×</button>
                        <div className="form-field" style={{ marginBottom: 8 }}>
                          <label>Description</label>
                          <input type="text" value={l.desc} onChange={e => updateLine(l.id, "desc", e.target.value)} placeholder="e.g. Regular Clean — 2 Bed" />
                        </div>
                        <div className="line-item-grid">
                          <div className="form-field" style={{ marginBottom: 0 }}>
                            <label>Unit Price ({currencySymbol})</label>
                            <input type="number" value={l.price} min="0" step="0.01" onChange={e => updateLine(l.id, "price", e.target.value)} />
                          </div>
                          <div className="form-field" style={{ marginBottom: 0 }}>
                            <label>Qty</label>
                            <input type="number" value={l.qty} min="1" onChange={e => updateLine(l.id, "qty", e.target.value)} />
                          </div>
                          <div className="form-field" style={{ marginBottom: 0 }}>
                            <label>Total</label>
                            <input type="text" value={fmt(l.price * l.qty, currencySymbol)} readOnly className="line-total-val" />
                          </div>
                        </div>
                      </div>
                    ))}
                  </div>
                  <button className="btn-add-line" onClick={() => addLine()}>+ Add Service Line</button>
                  <div style={{ display: "flex", gap: 8, marginTop: 8 }}>
                    <button className="btn-add-line" style={{ marginTop: 0 }} onClick={() => setShowTemplates(true)}>⚡ Load Template</button>
                    <button className="btn-add-line" style={{ marginTop: 0 }} onClick={() => setShowSaveTemplate(true)}>💾 Save as Template</button>
                  </div>
                </div>
                <div className="sidebar-section">
                  <div className="sidebar-label">Totals</div>
                  <div className="form-row">
                    <div className="form-field">
                      <label>VAT % (0 if N/A)</label>
                      <input type="number" value={state.vatRate} min="0" max="100" onChange={e => set("vatRate", e.target.value)} />
                    </div>
                    <div className="form-field">
                      <label>Discount ({currencySymbol})</label>
                      <input type="number" value={state.discount} min="0" onChange={e => set("discount", e.target.value)} />
                    </div>
                  </div>
                  <div className="form-field">
                    <label>Deposit Paid ({currencySymbol})</label>
                    <input type="number" value={state.depositPaid} min="0" onChange={e => set("depositPaid", e.target.value)} />
                    <div className="deposit-btns">
                      {[10, 25, 50].map(pct => (
                        <button key={pct} className="deposit-btn" onClick={() => setDeposit(pct)}>{pct}%</button>
                      ))}
                    </div>
                  </div>
                </div>
              </>
            )}

            {/* BUSINESS / SETTINGS TAB */}
            {activeTab === "settings" && (
              <div className="sidebar-section">
                <div className="sidebar-label">Your Business Info</div>
                <div className="form-field">
                  <label>Business Name</label>
                  <input type="text" value={state.bizName} onChange={e => set("bizName", e.target.value)} />
                </div>
                <div className="form-field">
                  <label>Address</label>
                  <textarea rows={2} value={state.bizAddress} onChange={e => set("bizAddress", e.target.value)} />
                </div>
                <div className="form-field">
                  <label>Email</label>
                  <input type="text" value={state.bizEmail} onChange={e => set("bizEmail", e.target.value)} />
                </div>
                <div className="form-field">
                  <label>Website</label>
                  <input type="text" value={state.bizWebsite} onChange={e => set("bizWebsite", e.target.value)} />
                </div>
                <div className="form-field">
                  <label>Account Name</label>
                  <input type="text" value={state.bankName} onChange={e => set("bankName", e.target.value)} />
                </div>
                <div className="form-row">
                  <div className="form-field">
                    <label>Sort Code</label>
                    <input type="text" value={state.bankSort} onChange={e => set("bankSort", e.target.value)} />
                  </div>
                  <div className="form-field">
                    <label>Account No.</label>
                    <input type="text" value={state.bankAcc} onChange={e => set("bankAcc", e.target.value)} />
                  </div>
                </div>
                <div className="form-field">
                  <label>Registered Info</label>
                  <textarea rows={2} value={state.bizReg} onChange={e => set("bizReg", e.target.value)} />
                </div>
              </div>
            )}
          </div>
        </aside>

        {/* PREVIEW */}
        <div className="preview-area">
          <div className="preview-label">INVOICE PREVIEW — LIVE EDIT</div>
          <div id="invoice-preview" ref={previewRef}>
            <div className="inv-header">
              <div>
                <div className="inv-logo-text">{state.bizName.toUpperCase() || "TOUCHSTONE"}</div>
                <span className="inv-logo-sub">C L E A N E R S</span>
              </div>
              <div className="inv-header-right">
                <div className="inv-number-label">INVOICE</div>
                <div className="inv-number">{state.invNumber}</div>
                <div className={`inv-status-badge ${state.status}`}>
                  {state.status.charAt(0).toUpperCase() + state.status.slice(1)}
                </div>
              </div>
            </div>
            <div style={{ height: 1, background: "linear-gradient(90deg,#C9A84C,transparent)", margin: "0" }} />
            <div className="inv-body">
              <div className="inv-meta">
                <div>
                  <div className="inv-meta-label">Date Issued</div>
                  <div className="inv-meta-value">{formatDate(state.invDate)}</div>
                </div>
                <div>
                  <div className="inv-meta-label">Payment Due</div>
                  <div className="inv-meta-value">{formatDate(state.invDue)}</div>
                </div>
                {state.invRef.trim() && (
                  <div>
                    <div className="inv-meta-label">Reference</div>
                    <div className="inv-meta-value">{state.invRef}</div>
                  </div>
                )}
              </div>
              <div className="inv-addresses">
                <div>
                  <div className="inv-address-label">From</div>
                  <div className="inv-address-name">{state.bizName}</div>
                  <div className="inv-address-text" dangerouslySetInnerHTML={{ __html: nl2br(state.bizAddress) }} />
                  <div className="inv-address-text" style={{ marginTop: 6 }}>{state.bizEmail}</div>
                  <div className="inv-address-text">{state.bizWebsite}</div>
                </div>
                <div>
                  <div className="inv-address-label">Bill To</div>
                  <div className="inv-address-name" style={!state.clientName ? { color: "#aaa", fontStyle: "italic" } : {}}>
                    {state.clientName || "Client Name"}
                  </div>
                  <div className="inv-address-text" style={!state.clientAddress ? { color: "#bbb" } : {}} dangerouslySetInnerHTML={{ __html: state.clientAddress ? nl2br(state.clientAddress) : "—" }} />
                  {state.clientEmail && <div className="inv-address-text" style={{ marginTop: 6 }}>{state.clientEmail}</div>}
                </div>
              </div>
              <table className="inv-table">
                <thead>
                  <tr>
                    <th style={{ width: "50%" }}>Description</th>
                    <th style={{ width: "12%" }}>Qty</th>
                    <th style={{ width: "19%" }}>Unit Price</th>
                    <th style={{ width: "19%" }}>Total</th>
                  </tr>
                </thead>
                <tbody>
                  {state.lineItems.length === 0 ? (
                    <tr><td colSpan={4} style={{ color: "#bbb", fontFamily: "var(--sans)", fontSize: 12, padding: "20px 0" }}>No services added yet.</td></tr>
                  ) : state.lineItems.map(l => (
                    <tr key={l.id}>
                      <td>{l.desc || <span style={{ color: "#ccc", fontStyle: "italic", fontSize: 13 }}>Unnamed service</span>}</td>
                      <td>{l.qty}</td>
                      <td>{fmt(l.price, currencySymbol)}</td>
                      <td>{fmt((parseFloat(l.qty) || 0) * (parseFloat(l.price) || 0), currencySymbol)}</td>
                    </tr>
                  ))}
                </tbody>
              </table>
              <div className="inv-totals">
                <div className="inv-totals-inner">
                  <div className="inv-total-row"><span className="inv-total-label">Subtotal</span><span className="inv-total-value">{fmt(subtotal, currencySymbol)}</span></div>
                  {disc > 0 && <div className="inv-total-row"><span className="inv-total-label">Discount</span><span className="inv-total-value" style={{ color: "#81c784" }}>−{fmt(disc, currencySymbol)}</span></div>}
                  {vatRate > 0 && <div className="inv-total-row"><span className="inv-total-label">VAT ({vatRate}%)</span><span className="inv-total-value">{fmt(vat, currencySymbol)}</span></div>}
                  {deposit > 0 && <div className="inv-total-row"><span className="inv-total-label">Deposit Paid</span><span className="inv-total-value" style={{ color: "#81c784" }}>−{fmt(deposit, currencySymbol)}</span></div>}
                  <div className="inv-total-row grand"><span className="inv-total-label">BALANCE DUE</span><span className="inv-total-value">{fmt(balanceDue, currencySymbol)}</span></div>
                </div>
              </div>
              <div className="inv-bottom">
                <div>
                  <div className="inv-notes-label">Notes</div>
                  <div className="inv-notes-text" dangerouslySetInnerHTML={{ __html: nl2br(state.notes) }} />
                </div>
                <div>
                  <div className="inv-bank-label">Bank Transfer Details</div>
                  <div className="inv-bank-row"><span className="inv-bank-key">Account Name</span><span className="inv-bank-val">{state.bankName}</span></div>
                  <div className="inv-bank-row"><span className="inv-bank-key">Sort Code</span><span className="inv-bank-val">{state.bankSort}</span></div>
                  <div className="inv-bank-row"><span className="inv-bank-key">Account No.</span><span className="inv-bank-val">{state.bankAcc}</span></div>
                </div>
              </div>
            </div>
            <div className="inv-footer">
              <div className="inv-footer-left" dangerouslySetInnerHTML={{ __html: nl2br(state.bizReg) }} />
              <div className="inv-footer-right">TOUCHSTONE</div>
            </div>
          </div>
          <div style={{ height: 48 }} />
        </div>
      </div>

      {/* KEYBOARD SHORTCUTS MODAL */}
      {showShortcuts && (
        <div className="modal-overlay" onClick={() => setShowShortcuts(false)}>
          <div className="modal" onClick={e => e.stopPropagation()} style={{ position: "relative" }}>
            <button className="modal-close" onClick={() => setShowShortcuts(false)}>×</button>
            <div className="modal-title">Keyboard Shortcuts</div>
            {[
              ["Ctrl + N", "New invoice"],
              ["Ctrl + Enter", "Download PDF"],
              ["Ctrl + Z", "Undo last change"],
              ["?", "Show this shortcuts panel"],
            ].map(([key, desc]) => (
              <div className="shortcut-row" key={key}>
                <span className="shortcut-key">{key}</span>
                <span className="shortcut-desc">{desc}</span>
              </div>
            ))}
            <p style={{ fontFamily: "var(--sans)", fontSize: 11, color: "rgba(255,255,255,0.3)", marginTop: 18, lineHeight: 1.6 }}>
              Tip: Use Tab to move between fields, and Delete/Backspace to clear values.
            </p>
          </div>
        </div>
      )}

      {/* TEMPLATES MODAL */}
      {showTemplates && (
        <div className="modal-overlay" onClick={() => setShowTemplates(false)}>
          <div className="modal" onClick={e => e.stopPropagation()} style={{ position: "relative" }}>
            <button className="modal-close" onClick={() => setShowTemplates(false)}>×</button>
            <div className="modal-title">Service Templates</div>
            <p style={{ fontFamily: "var(--sans)", fontSize: 11, color: "rgba(255,255,255,0.4)", marginBottom: 16, lineHeight: 1.6 }}>
              Click a template to add its services to your current invoice.
            </p>
            {Object.entries(tplGroups).map(([group, names]) => (
              <div key={group}>
                <div className="tpl-group">{group}</div>
                {names.map(name => {
                  const lines = SERVICE_TEMPLATES[name];
                  return (
                    <button key={name} className="tpl-btn" onClick={() => loadTemplate(name)}>
                      <span>{name.replace(/^[^–]+–\s*/, "")}</span>
                      <span className="tpl-price">{fmt(lines.reduce((s, l) => s + l.price * l.qty, 0), currencySymbol)}</span>
                    </button>
                  );
                })}
              </div>
            ))}
            {savedTplKeys.length > 0 && (
              <>
                <div className="tpl-group">MY SAVED TEMPLATES</div>
                {savedTplKeys.map(name => (
                  <button key={name} className="tpl-btn" onClick={() => loadTemplate(name)}>
                    <span>{name}</span>
                    <span className="tpl-price" style={{ fontSize: 10, opacity: 0.6 }}>saved</span>
                  </button>
                ))}
              </>
            )}
          </div>
        </div>
      )}

      {/* SAVE TEMPLATE MODAL */}
      {showSaveTemplate && (
        <div className="modal-overlay" onClick={() => setShowSaveTemplate(false)}>
          <div className="modal" onClick={e => e.stopPropagation()} style={{ position: "relative" }}>
            <button className="modal-close" onClick={() => setShowSaveTemplate(false)}>×</button>
            <div className="modal-title">Save as Template</div>
            <p style={{ fontFamily: "var(--sans)", fontSize: 12, color: "rgba(255,255,255,0.5)", marginBottom: 14 }}>
              Saves your current {state.lineItems.length} service line(s) as a reusable template.
            </p>
            <div className="form-field">
              <label>Template Name</label>
              <input type="text" value={templateNameInput} placeholder="e.g. My Standard Package" onChange={e => setTemplateNameInput(e.target.value)} onKeyDown={e => e.key === "Enter" && saveCurrentAsTemplate()} autoFocus />
            </div>
            <button className="btn-gold" style={{ marginTop: 12, width: "100%" }} onClick={saveCurrentAsTemplate}>Save Template</button>
          </div>
        </div>
      )}

      {/* SNIPPETS MODAL */}
      {showSnippets && (
        <div className="modal-overlay" onClick={() => setShowSnippets(false)}>
          <div className="modal" onClick={e => e.stopPropagation()} style={{ position: "relative" }}>
            <button className="modal-close" onClick={() => setShowSnippets(false)}>×</button>
            <div className="modal-title">Note Snippets</div>
            {NOTES_SNIPPETS.map((s, i) => (
              <button key={i} className="snippet-btn" onClick={() => { set("notes", state.notes ? state.notes + "\n\n" + s : s); setShowSnippets(false); }}>
                {s}
              </button>
            ))}
          </div>
        </div>
      )}

      {/* VALIDATION MODAL */}
      {showValidation && (
        <div className="modal-overlay" onClick={() => setShowValidation(false)}>
          <div className="modal" onClick={e => e.stopPropagation()} style={{ position: "relative" }}>
            <button className="modal-close" onClick={() => setShowValidation(false)}>×</button>
            <div className="modal-title" style={{ color: "#ef9a9a" }}>⚠ Before You Download</div>
            <p style={{ fontFamily: "var(--sans)", fontSize: 12, color: "rgba(255,255,255,0.5)", marginBottom: 14 }}>
              Please fix the following before generating your PDF:
            </p>
            {validationErrors.map((e, i) => <div key={i} className="validation-error">· {e}</div>)}
            <button className="btn-gold" style={{ marginTop: 14, width: "100%" }} onClick={() => setShowValidation(false)}>Got it</button>
          </div>
        </div>
      )}
    </div>
  );
}
