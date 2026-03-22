/**
 * @license
 * SPDX-License-Identifier: Apache-2.0
 */

import React, { useState, useEffect, useRef } from 'react';
import { 
  Menu, 
  X, 
  ChevronRight, 
  PlayCircle, 
  Bolt, 
  Diamond, 
  Brain, 
  FileText, 
  Zap, 
  ShieldCheck, 
  Cpu, 
  Share2, 
  History, 
  Copy, 
  Check,
  Briefcase,
  MessageCircle,
  Brush,
  GraduationCap,
  Verified,
  Settings2,
  Waves,
  Link2,
  PenTool,
  Clipboard,
  Trash2
} from 'lucide-react';
import { motion, AnimatePresence } from 'motion/react';
import { humanizeText } from './lib/gemini';

type Page = 'home' | 'humanizer' | 'how-it-works';

export default function App() {
  const [currentPage, setCurrentPage] = useState<Page>('home');
  const [isMenuOpen, setIsMenuOpen] = useState(false);

  // Scroll to top on page change
  useEffect(() => {
    window.scrollTo(0, 0);
  }, [currentPage]);

  return (
    <div className="min-h-screen flex flex-col">
      {/* Navigation */}
      <nav className="fixed top-0 w-full z-50 bg-surface/80 backdrop-blur-xl border-b border-outline/10">
        <div className="max-w-7xl mx-auto px-6 h-20 flex items-center justify-between">
          <div 
            className="text-2xl font-bold text-primary font-headline tracking-tighter cursor-pointer"
            onClick={() => setCurrentPage('home')}
          >
            Humanist Logic
          </div>

          {/* Desktop Nav */}
          <div className="hidden md:flex items-center space-x-8 font-headline font-medium">
            <button 
              onClick={() => setCurrentPage('humanizer')}
              className={`transition-colors relative py-1 ${currentPage === 'humanizer' ? 'text-primary' : 'text-on-surface-variant hover:text-primary'}`}
            >
              Humanizer
              {currentPage === 'humanizer' && (
                <motion.div layoutId="nav-underline" className="absolute bottom-0 left-0 right-0 h-0.5 bg-primary" />
              )}
            </button>
            <button 
              onClick={() => setCurrentPage('how-it-works')}
              className={`transition-colors relative py-1 ${currentPage === 'how-it-works' ? 'text-primary' : 'text-on-surface-variant hover:text-primary'}`}
            >
              How It Works
              {currentPage === 'how-it-works' && (
                <motion.div layoutId="nav-underline" className="absolute bottom-0 left-0 right-0 h-0.5 bg-primary" />
              )}
            </button>
          </div>

          <div className="hidden md:flex items-center space-x-4">
            <button className="px-5 py-2 text-on-surface-variant font-medium hover:bg-surface-container-low rounded-lg transition-colors">
              Login
            </button>
            <button 
              onClick={() => setCurrentPage('humanizer')}
              className="px-6 py-2.5 humanizer-gradient text-white font-semibold rounded-lg shadow-lg hover:shadow-xl active:scale-95 transition-transform"
            >
              Try Free
            </button>
          </div>

          {/* Mobile Menu Toggle */}
          <button className="md:hidden p-2" onClick={() => setIsMenuOpen(!isMenuOpen)}>
            {isMenuOpen ? <X /> : <Menu />}
          </button>
        </div>

        {/* Mobile Nav */}
        <AnimatePresence>
          {isMenuOpen && (
            <motion.div 
              initial={{ opacity: 0, y: -20 }}
              animate={{ opacity: 1, y: 0 }}
              exit={{ opacity: 0, y: -20 }}
              className="md:hidden bg-surface border-b border-outline/10 px-6 py-8 space-y-4"
            >
              <button 
                onClick={() => { setCurrentPage('humanizer'); setIsMenuOpen(false); }}
                className="block w-full text-left text-lg font-medium text-on-surface-variant"
              >
                Humanizer
              </button>
              <button 
                onClick={() => { setCurrentPage('how-it-works'); setIsMenuOpen(false); }}
                className="block w-full text-left text-lg font-medium text-on-surface-variant"
              >
                How It Works
              </button>
              <div className="pt-4 flex flex-col space-y-4">
                <button className="w-full py-3 text-center font-medium border border-outline/20 rounded-lg">Login</button>
                <button 
                  onClick={() => { setCurrentPage('humanizer'); setIsMenuOpen(false); }}
                  className="w-full py-3 text-center humanizer-gradient text-white font-bold rounded-lg"
                >
                  Try Free
                </button>
              </div>
            </motion.div>
          )}
        </AnimatePresence>
      </nav>

      {/* Page Content */}
      <main className="flex-grow pt-20">
        <AnimatePresence mode="wait">
          {currentPage === 'home' && (
            <motion.div key="home" initial={{ opacity: 0 }} animate={{ opacity: 1 }} exit={{ opacity: 0 }}>
              <HomePage onStart={() => setCurrentPage('humanizer')} onHowItWorks={() => setCurrentPage('how-it-works')} />
            </motion.div>
          )}
          {currentPage === 'humanizer' && (
            <motion.div key="humanizer" initial={{ opacity: 0 }} animate={{ opacity: 1 }} exit={{ opacity: 0 }}>
              <HumanizerPage />
            </motion.div>
          )}
          {currentPage === 'how-it-works' && (
            <motion.div key="how-it-works" initial={{ opacity: 0 }} animate={{ opacity: 1 }} exit={{ opacity: 0 }}>
              <HowItWorksPage onStart={() => setCurrentPage('humanizer')} />
            </motion.div>
          )}
        </AnimatePresence>
      </main>

      {/* Footer */}
      <footer className="bg-surface-container-low py-16 border-t border-outline/10">
        <div className="max-w-7xl mx-auto px-8 grid grid-cols-1 md:grid-cols-4 gap-12">
          <div className="col-span-1 md:col-span-1">
            <div className="text-xl font-bold text-primary font-headline tracking-tighter mb-4">Humanist Logic</div>
            <p className="text-on-surface-variant text-sm leading-relaxed">
              Elevating the world's text through the perfect union of machine logic and human soul. Precision meets craft.
            </p>
            <p className="mt-8 text-outline text-xs">© 2024 Humanist Logic. All rights reserved.</p>
          </div>
          <div>
            <h4 className="font-headline font-bold mb-6">Product</h4>
            <ul className="space-y-3 text-sm text-on-surface-variant">
              <li><button onClick={() => setCurrentPage('humanizer')} className="hover:text-primary transition-colors">Humanizer</button></li>
              <li><button onClick={() => setCurrentPage('how-it-works')} className="hover:text-primary transition-colors">How It Works</button></li>
              <li><a href="#" className="hover:text-primary transition-colors">Pricing</a></li>
              <li><a href="#" className="hover:text-primary transition-colors">API Docs</a></li>
            </ul>
          </div>
          <div>
            <h4 className="font-headline font-bold mb-6">Company</h4>
            <ul className="space-y-3 text-sm text-on-surface-variant">
              <li><a href="#" className="hover:text-primary transition-colors">Privacy Policy</a></li>
              <li><a href="#" className="hover:text-primary transition-colors">Terms of Service</a></li>
              <li><a href="#" className="hover:text-primary transition-colors">Contact Us</a></li>
              <li><a href="#" className="hover:text-primary transition-colors">About Us</a></li>
            </ul>
          </div>
          <div>
            <h4 className="font-headline font-bold mb-6">Resources</h4>
            <ul className="space-y-3 text-sm text-on-surface-variant">
              <li><a href="#" className="hover:text-primary transition-colors">Documentation</a></li>
              <li><a href="#" className="text-primary font-medium flex items-center gap-2">Status <div className="w-2 h-2 rounded-full bg-emerald-500 animate-pulse" /></a></li>
              <li><a href="#" className="hover:text-primary transition-colors">Twitter</a></li>
              <li><a href="#" className="hover:text-primary transition-colors">LinkedIn</a></li>
            </ul>
          </div>
        </div>
      </footer>
    </div>
  );
}

// --- Page Components ---

function HomePage({ onStart, onHowItWorks }: { onStart: () => void, onHowItWorks: () => void }) {
  return (
    <div className="space-y-24 pb-24">
      {/* Hero */}
      <section className="max-w-7xl mx-auto px-8 pt-20 grid md:grid-cols-12 gap-12 items-center">
        <div className="md:col-span-7">
          <motion.span 
            initial={{ opacity: 0, y: 10 }}
            animate={{ opacity: 1, y: 0 }}
            className="inline-flex items-center px-3 py-1 rounded-full bg-primary/10 text-primary text-xs font-bold tracking-widest uppercase mb-6"
          >
            The Future of Craft
          </motion.span>
          <motion.h1 
            initial={{ opacity: 0, y: 20 }}
            animate={{ opacity: 1, y: 0 }}
            transition={{ delay: 0.1 }}
            className="font-headline text-5xl md:text-7xl font-extrabold text-on-surface leading-[1.1] tracking-tight mb-8"
          >
            Turn AI Text Into <span className="text-primary">Human Gold.</span>
          </motion.h1>
          <motion.p 
            initial={{ opacity: 0, y: 20 }}
            animate={{ opacity: 1, y: 0 }}
            transition={{ delay: 0.2 }}
            className="text-lg md:text-xl text-on-surface-variant max-w-xl mb-10 leading-relaxed"
          >
            Precision engineering meets human artistry. Our logic-driven engine bypasses detection while maintaining the soulful nuance of elite writing.
          </motion.p>
          <motion.div 
            initial={{ opacity: 0, y: 20 }}
            animate={{ opacity: 1, y: 0 }}
            transition={{ delay: 0.3 }}
            className="flex flex-col sm:flex-row gap-4"
          >
            <button 
              onClick={onStart}
              className="px-8 py-4 humanizer-gradient text-white font-bold rounded-xl text-lg shadow-xl hover:shadow-2xl transition-all active:scale-95"
            >
              Humanize Your Text Now
            </button>
            <button 
              onClick={onHowItWorks}
              className="px-8 py-4 bg-surface-container-low text-on-surface font-semibold rounded-xl text-lg hover:bg-surface-container-high transition-all flex items-center justify-center gap-2"
            >
              <PlayCircle className="w-5 h-5" />
              See How It Works
            </button>
          </motion.div>
        </div>
        <div className="md:col-span-5 relative">
          <div className="absolute -top-20 -right-20 w-80 h-80 bg-primary/5 rounded-full blur-3xl" />
          <motion.div 
            initial={{ opacity: 0, scale: 0.9, rotate: 0 }}
            animate={{ opacity: 1, scale: 1, rotate: 2 }}
            transition={{ delay: 0.4, type: 'spring' }}
            className="relative glass-panel border border-outline/10 rounded-3xl p-6 shadow-2xl"
          >
            <div className="flex items-center gap-2 mb-6">
              <div className="w-3 h-3 rounded-full bg-red-400/40" />
              <div className="w-3 h-3 rounded-full bg-amber-400/40" />
              <div className="w-3 h-3 rounded-full bg-emerald-400/40" />
            </div>
            <div className="space-y-4">
              <div className="h-4 w-3/4 bg-surface-container-low rounded-full" />
              <div className="h-4 w-full bg-surface-container-low rounded-full" />
              <div className="h-4 w-5/6 bg-surface-container-low rounded-full" />
              <div className="pt-6 flex justify-between items-center border-t border-outline/5">
                <div className="flex gap-2">
                  <div className="px-3 py-1 bg-primary/10 text-primary text-[10px] font-bold rounded-full uppercase tracking-wider">98% HUMAN</div>
                  <div className="px-3 py-1 bg-surface-container-low text-on-surface-variant text-[10px] font-bold rounded-full uppercase tracking-wider">LOGIC v4.2</div>
                </div>
                <Verified className="w-5 h-5 text-primary" />
              </div>
            </div>
          </motion.div>
        </div>
      </section>

      {/* Precision Crafting */}
      <section className="bg-surface-container-low py-24 px-8">
        <div className="max-w-7xl mx-auto">
          <div className="mb-16">
            <h2 className="font-headline text-3xl md:text-5xl font-bold text-on-surface mb-4">Precision Crafting</h2>
            <p className="text-on-surface-variant text-lg max-w-2xl">The bridge between artificial speed and human depth.</p>
          </div>
          <div className="grid grid-cols-1 md:grid-cols-3 gap-8">
            <FeatureCard 
              icon={<Bolt className="w-8 h-8 text-primary" />}
              title="Instant Speed"
              description="Large-scale transformation in seconds. Our distributed logic engine processes thousands of words without breaking a sweat."
            />
            <FeatureCard 
              icon={<Diamond className="w-8 h-8 text-primary" />}
              title="Elite Quality"
              description="We don't just swap synonyms. We restructure syntax, adjust cadence, and inject semantic variety that fools even the toughest tools."
            />
            <FeatureCard 
              icon={<Brain className="w-8 h-8 text-primary" />}
              title="Natural Tone"
              description="Choose your persona. From academic rigor to conversational flair, our AI adapts to your specific brand voice perfectly."
            />
          </div>
        </div>
      </section>

      {/* Tool Preview */}
      <section className="py-24 px-8 max-w-7xl mx-auto">
        <div className="text-center mb-16">
          <h2 className="font-headline text-4xl md:text-5xl font-extrabold mb-6">Experience the Logic</h2>
          <p className="text-on-surface-variant text-xl">The workspace for craft. Transform your text below.</p>
        </div>
        <div className="bg-surface-container-lowest rounded-[2.5rem] border border-outline/10 p-4 md:p-8 shadow-2xl">
          <div className="grid md:grid-cols-2 gap-8 min-h-[400px]">
            <div className="flex flex-col">
              <div className="flex items-center justify-between mb-4 px-2">
                <label className="text-xs font-bold tracking-widest text-on-surface-variant uppercase">Input AI Draft</label>
                <span className="text-xs text-outline">0 / 5000 words</span>
              </div>
              <div className="flex-grow w-full bg-surface rounded-2xl p-6 text-lg text-outline/50 italic border border-outline/5">
                Paste your AI-generated text here...
              </div>
            </div>
            <div className="flex flex-col relative rounded-2xl overflow-hidden bg-primary/5 border border-primary/10">
              <div className="absolute inset-0 bg-white/40 backdrop-blur-sm z-0" />
              <div className="relative z-10 p-6 flex flex-col h-full">
                <div className="flex items-center justify-between mb-4">
                  <label className="text-xs font-bold tracking-widest text-primary uppercase">Humanized Output</label>
                  <div className="flex gap-2">
                    <div className="p-2 bg-white/50 rounded-lg"><Copy className="w-4 h-4 text-primary/60" /></div>
                    <div className="p-2 bg-white/50 rounded-lg"><Share2 className="w-4 h-4 text-primary/60" /></div>
                  </div>
                </div>
                <div className="flex-grow flex items-center justify-center text-center p-8">
                  <div className="space-y-4">
                    <Zap className="w-12 h-12 text-primary mx-auto animate-pulse" />
                    <p className="text-on-surface-variant italic">Waiting for your masterpiece...</p>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div className="mt-8 flex flex-col md:flex-row items-center justify-between gap-6 bg-surface-container-low p-6 rounded-2xl">
            <div className="flex flex-wrap gap-3">
              <div className="px-5 py-2 bg-primary/10 text-primary rounded-full text-sm font-semibold flex items-center gap-2">
                <GraduationCap className="w-4 h-4" /> Academic
              </div>
              <div className="px-5 py-2 bg-surface rounded-full text-sm font-semibold text-on-surface-variant flex items-center gap-2">
                <MessageCircle className="w-4 h-4" /> Conversational
              </div>
              <div className="px-5 py-2 bg-surface rounded-full text-sm font-semibold text-on-surface-variant flex items-center gap-2">
                <Briefcase className="w-4 h-4" /> Professional
              </div>
            </div>
            <button 
              onClick={onStart}
              className="w-full md:w-auto px-10 py-4 humanizer-gradient text-white font-bold rounded-xl shadow-lg hover:scale-[1.02] active:scale-95 transition-all"
            >
              Humanize Selection
            </button>
          </div>
        </div>
      </section>

      {/* Final CTA */}
      <section className="px-8 max-w-7xl mx-auto">
        <div className="bg-primary rounded-[3rem] p-12 md:p-20 text-center relative overflow-hidden">
          <div className="absolute top-0 right-0 w-96 h-96 bg-white/5 rounded-full blur-3xl -translate-y-1/2 translate-x-1/2" />
          <h2 className="font-headline text-4xl md:text-6xl font-extrabold text-white mb-8 relative z-10">Ready to humanize your output?</h2>
          <div className="flex justify-center relative z-10">
            <button 
              onClick={onStart}
              className="px-10 py-5 bg-white text-primary font-bold rounded-2xl text-xl shadow-xl hover:shadow-2xl transition-all active:scale-95"
            >
              Get Started Free
            </button>
          </div>
        </div>
      </section>
    </div>
  );
}

function HumanizerPage() {
  const [input, setInput] = useState('');
  const [output, setOutput] = useState('');
  const [isProcessing, setIsProcessing] = useState(false);
  const [tone, setTone] = useState('Professional');
  const [intensity, setIntensity] = useState(85);
  const [copied, setCopied] = useState(false);
  const textareaRef = useRef<HTMLTextAreaElement>(null);

  // Focus textarea on mount
  useEffect(() => {
    textareaRef.current?.focus();
  }, []);

  const handleHumanize = async (textToProcess = input) => {
    if (!textToProcess.trim()) {
      setOutput('');
      return;
    }
    setIsProcessing(true);
    const intensityLabel = intensity < 33 ? 'Subtle' : intensity < 66 ? 'Standard' : 'Deep';
    const result = await humanizeText(textToProcess, tone, intensityLabel);
    setOutput(result);
    setIsProcessing(false);
  };

  // Auto-humanize with debounce
  useEffect(() => {
    const timer = setTimeout(() => {
      if (input.trim()) {
        handleHumanize(input);
      }
    }, 800); // 800ms debounce

    return () => clearTimeout(timer);
  }, [input, tone, intensity]);

  const copyToClipboard = () => {
    navigator.clipboard.writeText(output);
    setCopied(true);
    setTimeout(() => setCopied(false), 2000);
  };

  const handlePaste = async () => {
    try {
      const text = await navigator.clipboard.readText();
      if (text) {
        setInput(text);
        handleHumanize(text); // Immediate trigger on paste
      }
    } catch (err) {
      console.error('Failed to read clipboard:', err);
      // Fallback: focus the textarea and let the user paste manually
      textareaRef.current?.focus();
      // We could show a toast here if we had one
    }
  };

  return (
    <div className="max-w-7xl mx-auto px-8 pb-24">
      <header className="mb-12 pt-12">
        <h1 className="font-headline text-4xl md:text-5xl font-extrabold tracking-tight text-on-surface max-w-2xl leading-tight">
          Crafting AI output with <span className="text-primary-container">editorial precision.</span>
        </h1>
        <p className="text-on-surface-variant mt-4 text-lg max-w-xl">
          Transform robotic syntax into sophisticated, human-centric prose. High-fidelity logic, humanized for the modern workspace.
        </p>
      </header>

      <div className="grid grid-cols-12 gap-8 items-start">
        {/* Sidebar */}
        <aside className="col-span-12 lg:col-span-3 space-y-6">
          <div className="bg-surface-container-low p-6 rounded-xl space-y-8">
            <div>
              <label className="block font-headline text-xs font-bold uppercase tracking-widest text-on-surface-variant mb-4">Artistic Tone</label>
              <div className="grid grid-cols-1 gap-2">
                {[
                  { name: 'Professional', icon: <Briefcase className="w-4 h-4" /> },
                  { name: 'Casual', icon: <MessageCircle className="w-4 h-4" /> },
                  { name: 'Creative', icon: <Brush className="w-4 h-4" /> },
                  { name: 'Academic', icon: <GraduationCap className="w-4 h-4" /> },
                ].map((t) => (
                  <button 
                    key={t.name}
                    onClick={() => setTone(t.name)}
                    className={`flex items-center gap-3 w-full p-3 rounded-lg transition-all font-medium ${tone === t.name ? 'bg-surface-container-lowest text-primary border-2 border-primary/10 shadow-sm' : 'hover:bg-surface-container-highest text-on-surface-variant'}`}
                  >
                    {t.icon}
                    {t.name}
                  </button>
                ))}
              </div>
            </div>

            <div className="space-y-4">
              <div className="flex justify-between items-center">
                <label className="font-headline text-xs font-bold uppercase tracking-widest text-on-surface-variant">Intensity</label>
                <span className="text-[10px] font-bold text-primary px-2 py-1 bg-primary/10 rounded-full uppercase">
                  {intensity < 33 ? 'Subtle' : intensity < 66 ? 'Standard' : 'Deep'}
                </span>
              </div>
              <input 
                type="range" 
                min="0" 
                max="100" 
                value={intensity}
                onChange={(e) => setIntensity(parseInt(e.target.value))}
                className="w-full h-2 bg-surface-container-highest rounded-lg appearance-none cursor-pointer accent-primary"
              />
              <div className="flex justify-between text-[10px] font-bold text-outline uppercase tracking-tighter">
                <span>Subtle</span>
                <span>Standard</span>
                <span>Deep</span>
              </div>
            </div>
          </div>

          <div className="bg-primary/5 p-6 rounded-xl border border-primary/10">
            <div className="flex items-center gap-2 text-primary font-bold mb-2">
              <ShieldCheck className="w-4 h-4" />
              <span className="text-sm">Human Logic Guard</span>
            </div>
            <p className="text-xs text-on-surface-variant leading-relaxed">
              Currently processing with V4 Engine. Precision-tuned for undetectable semantic flow.
            </p>
          </div>
        </aside>

        {/* Main Tool */}
        <div className="col-span-12 lg:col-span-9 space-y-8">
          <div className="grid grid-cols-1 md:grid-cols-2 gap-6">
            {/* Input */}
            <div className="flex flex-col h-[500px] bg-surface-container-lowest rounded-xl shadow-sm overflow-hidden border border-outline/5 focus-within:border-primary/30 transition-colors">
              <div className="px-6 py-4 flex justify-between items-center bg-surface-container-low/50">
                <div className="flex items-center gap-4">
                  <span className="text-xs font-bold uppercase tracking-widest text-on-surface-variant">Input Canvas</span>
                  <button 
                    onClick={handlePaste}
                    className="px-3 py-1.5 bg-primary/10 text-primary rounded-lg text-[10px] font-bold uppercase tracking-widest hover:bg-primary/20 transition-colors flex items-center gap-1.5"
                  >
                    <Clipboard className="w-3.5 h-3.5" /> Paste Content
                  </button>
                  <button 
                    onClick={() => setInput('')}
                    className="px-3 py-1.5 bg-surface-container-highest text-outline rounded-lg text-[10px] font-bold uppercase tracking-widest hover:text-on-surface-variant transition-colors flex items-center gap-1.5"
                  >
                    <Trash2 className="w-3.5 h-3.5" /> Clear
                  </button>
                </div>
                <span className="text-xs text-outline">{input.split(/\s+/).filter(Boolean).length} / 2,500 words</span>
              </div>
              <textarea 
                ref={textareaRef}
                value={input}
                onChange={(e) => setInput(e.target.value)}
                onPaste={(e) => {
                  const text = e.clipboardData.getData('text');
                  if (text) {
                    handleHumanize(text);
                  }
                }}
                className="flex-1 w-full p-6 bg-transparent border-none focus:ring-0 resize-none text-on-surface placeholder:text-outline/50 leading-relaxed text-lg outline-none" 
                placeholder="Paste your AI-generated draft here..."
                autoFocus
              />
              <div className="p-4 bg-surface-container-low/30 border-t border-outline/5 flex justify-end">
                <button 
                  onClick={() => handleHumanize()}
                  disabled={isProcessing || !input.trim()}
                  className="humanizer-gradient text-white px-8 py-3 rounded-lg font-headline font-bold flex items-center gap-2 hover:scale-[1.02] active:scale-95 transition-all shadow-lg disabled:opacity-50 disabled:scale-100"
                >
                  {isProcessing ? 'Processing...' : 'Humanize Logic'}
                  <Zap className={`w-4 h-4 ${isProcessing ? 'animate-spin' : ''}`} />
                </button>
              </div>
            </div>

            {/* Output */}
            <div className="flex flex-col h-[500px] bg-surface-container-low rounded-xl shadow-sm overflow-hidden border border-outline/5">
              <div className="px-6 py-4 flex justify-between items-center bg-surface-container-high/40">
                <span className="text-xs font-bold uppercase tracking-widest text-on-surface-variant">Refined Output</span>
                <div className="flex items-center gap-2">
                  <span className="text-[10px] font-bold text-on-surface-variant uppercase">Human Score</span>
                  <div className="bg-emerald-100 text-emerald-700 px-2 py-0.5 rounded text-xs font-black">98%</div>
                </div>
              </div>
              <div className="flex-1 p-6 overflow-y-auto bg-surface-container-lowest/40 backdrop-blur-sm relative">
                {isProcessing ? (
                  <div className="absolute inset-0 flex items-center justify-center bg-white/50">
                    <div className="flex flex-col items-center gap-4">
                      <div className="w-12 h-12 border-4 border-primary border-t-transparent rounded-full animate-spin" />
                      <p className="text-primary font-medium animate-pulse">Humanizing your prose...</p>
                    </div>
                  </div>
                ) : output ? (
                  <div className="text-on-surface leading-relaxed text-lg whitespace-pre-wrap">
                    {output}
                  </div>
                ) : (
                  <p className="text-on-surface-variant italic text-center mt-32">
                    Your refined content will appear here after processing.
                  </p>
                )}
              </div>
              <div className="p-4 bg-surface-container-high/40 border-t border-outline/5 flex justify-between items-center">
                <div className="flex gap-2">
                  <button className="p-2 hover:bg-surface-container-highest rounded-lg transition-colors text-on-surface-variant">
                    <Share2 className="w-5 h-5" />
                  </button>
                  <button className="p-2 hover:bg-surface-container-highest rounded-lg transition-colors text-on-surface-variant">
                    <History className="w-5 h-5" />
                  </button>
                </div>
                <button 
                  onClick={copyToClipboard}
                  disabled={!output}
                  className="bg-on-surface text-surface px-6 py-2 rounded-lg font-medium text-sm flex items-center gap-2 hover:opacity-90 active:scale-95 transition-all disabled:opacity-50"
                >
                  {copied ? 'Copied!' : 'Copy Result'}
                  {copied ? <Check className="w-4 h-4" /> : <Copy className="w-4 h-4" />}
                </button>
              </div>
            </div>
          </div>

          {/* Features */}
          <div className="grid grid-cols-1 md:grid-cols-3 gap-6">
            <div className="p-6 bg-surface-container-low rounded-xl border border-outline/5">
              <div className="w-10 h-10 rounded-full bg-primary/10 flex items-center justify-center text-primary mb-4">
                <FileText className="w-5 h-5" />
              </div>
              <h4 className="font-headline font-bold text-on-surface mb-2">Semantic Flow</h4>
              <p className="text-sm text-on-surface-variant">Re-engineers sentence structure to mimic natural human variation and rhythm.</p>
            </div>
            <div className="p-6 bg-surface-container-low rounded-xl border border-outline/5">
              <div className="w-10 h-10 rounded-full bg-primary/10 flex items-center justify-center text-primary mb-4">
                <ShieldCheck className="w-5 h-5" />
              </div>
              <h4 className="font-headline font-bold text-on-surface mb-2">Anti-Detection</h4>
              <p className="text-sm text-on-surface-variant">Optimized to pass through all major AI linguistic classifiers with 99% accuracy.</p>
            </div>
            <div className="p-6 bg-surface-container-low rounded-xl border border-outline/5">
              <div className="w-10 h-10 rounded-full bg-primary/10 flex items-center justify-center text-primary mb-4">
                <Cpu className="w-5 h-5" />
              </div>
              <h4 className="font-headline font-bold text-on-surface mb-2">Logic Preservation</h4>
              <p className="text-sm text-on-surface-variant">Ensures your original arguments and data remain intact during translation.</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  );
}

function HowItWorksPage({ onStart }: { onStart: () => void }) {
  return (
    <div className="pb-24">
      {/* Hero */}
      <section className="max-w-7xl mx-auto px-8 py-20">
        <div className="max-w-3xl">
          <span className="inline-block px-4 py-1 rounded-full bg-primary/10 text-primary text-sm font-semibold mb-6">Process & Philosophy</span>
          <h1 className="text-6xl md:text-7xl font-headline font-extrabold tracking-tight leading-tight text-on-surface mb-8">
            Where Artificial Intelligence meets <span className="text-primary italic">Human Craft.</span>
          </h1>
          <p className="text-xl text-on-surface-variant leading-relaxed max-w-2xl">
            We don't just "spin" text. We dismantle the cold, predictable patterns of large language models and rebuild them with the nuance, rhythm, and intentionality of professional editors.
          </p>
        </div>
      </section>

      {/* Workflow */}
      <section className="max-w-7xl mx-auto px-8 mb-40">
        <div className="mb-12">
          <h2 className="text-3xl font-headline font-bold mb-4">Workflow of Craft</h2>
          <div className="h-1 w-20 bg-primary rounded-full" />
        </div>
        <div className="grid grid-cols-1 md:grid-cols-3 gap-6">
          <WorkflowStep 
            number="01"
            icon={<Copy className="w-6 h-6 text-primary" />}
            title="Paste Text"
            description="Input any AI-generated output. Our system accepts long-form essays, emails, or technical documentation up to 5,000 words."
          />
          <WorkflowStep 
            number="02"
            icon={<Zap className="w-6 h-6 text-white" />}
            title="AI Humanizing Magic"
            description="The Logic Engine executes thousands of micro-adjustments per paragraph, breaking machine monotony while preserving your core message."
            accent
          />
          <WorkflowStep 
            number="03"
            icon={<Verified className="w-6 h-6 text-primary" />}
            title="Perfect Content"
            description="Export text that passes as human-written in any detection suite. Ready for publication, submission, or sensitive communication."
          />
        </div>
      </section>

      {/* Deep Dive */}
      <section className="bg-surface-container-low py-32 mb-40">
        <div className="max-w-7xl mx-auto px-8 grid md:grid-cols-2 gap-16 items-center">
          <div className="relative">
            <div className="absolute -top-12 -left-12 w-64 h-64 bg-primary/5 rounded-full blur-3xl" />
            <h2 className="text-4xl font-headline font-bold text-on-surface mb-8 leading-tight">
              The Logic Engine:<br /><span className="text-primary">Under the Hood</span>
            </h2>
            <p className="text-lg text-on-surface-variant mb-12">
              Traditional bypass tools simply swap synonyms. Our engine performs a deep semantic scan to restructure the DNA of the text.
            </p>
            <div className="space-y-8">
              <DeepDiveItem 
                icon={<Brain className="w-6 h-6 text-primary" />}
                title="Semantic Analysis"
                description="Identifies the underlying 'intent' of your writing before any transformation occurs."
              />
              <DeepDiveItem 
                icon={<Settings2 className="w-6 h-6 text-primary" />}
                title="Tone Alignment"
                description="Matches the output to specific human archetypes—from academic precision to casual banter."
              />
              <DeepDiveItem 
                icon={<Waves className="w-6 h-6 text-primary" />}
                title="Burstiness Control"
                description="Injects sentence length variation, a hallmark of human-authored prose that machines struggle to replicate."
              />
              <DeepDiveItem 
                icon={<Link2 className="w-6 h-6 text-primary" />}
                title="Contextual Flow"
                description="Ensures transitions between ideas feel organic and logical, rather than abrupt or repetitive."
              />
            </div>
          </div>
          <div className="relative">
            <div className="aspect-square glass-panel rounded-2xl shadow-2xl p-2 border border-white/40 overflow-hidden">
              <div className="w-full h-full rounded-xl bg-surface-container-highest relative overflow-hidden">
                <img 
                  src="https://picsum.photos/seed/ai-logic/800/800" 
                  alt="AI Logic Visualization" 
                  className="w-full h-full object-cover opacity-40 mix-blend-multiply"
                  referrerPolicy="no-referrer"
                />
                <div className="absolute inset-0 flex items-center justify-center p-8">
                  <div className="bg-white/90 backdrop-blur-md p-8 rounded-xl shadow-lg border border-primary/10 w-full max-w-sm">
                    <div className="flex items-center gap-3 mb-6">
                      <div className="w-3 h-3 rounded-full bg-red-500 animate-pulse" />
                      <span className="text-[10px] font-bold tracking-widest uppercase text-on-surface-variant">Real-time Processing</span>
                    </div>
                    <div className="space-y-4">
                      <div className="h-2 w-full bg-primary/10 rounded-full overflow-hidden">
                        <motion.div 
                          initial={{ width: 0 }}
                          animate={{ width: '100%' }}
                          transition={{ duration: 2, repeat: Infinity }}
                          className="h-full bg-primary"
                        />
                      </div>
                      <div className="h-2 w-3/4 bg-primary/10 rounded-full" />
                      <div className="h-2 w-5/6 bg-primary/10 rounded-full" />
                    </div>
                    <div className="mt-8 flex justify-between items-center">
                      <span className="text-sm font-medium text-primary">Scanning Syntax...</span>
                      <span className="text-sm font-bold">98% Human Match</span>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>

      {/* CTA */}
      <section className="max-w-5xl mx-auto px-8">
        <div className="humanizer-gradient rounded-3xl p-16 text-center text-white relative overflow-hidden">
          <div className="absolute top-0 right-0 p-12 opacity-10">
            <PenTool className="w-48 h-48" />
          </div>
          <h2 className="text-4xl font-headline font-extrabold mb-6 relative z-10">Ready to humanize your output?</h2>
          <p className="text-xl text-blue-100 mb-10 max-w-2xl mx-auto relative z-10">Join over 10,000 creators who prioritize craft over clicks.</p>
          <div className="flex justify-center relative z-10">
            <button 
              onClick={onStart}
              className="bg-white text-primary px-8 py-4 rounded-xl font-bold text-lg hover:bg-blue-50 transition-colors shadow-lg active:scale-95"
            >
              Get Started Free
            </button>
          </div>
        </div>
      </section>
    </div>
  );
}

// --- Helper Components ---

function FeatureCard({ icon, title, description }: { icon: React.ReactNode, title: string, description: string }) {
  return (
    <div className="bg-surface-container-lowest p-10 rounded-[2rem] shadow-sm hover:shadow-md transition-shadow group">
      <div className="w-14 h-14 bg-primary/5 rounded-2xl flex items-center justify-center mb-8 group-hover:scale-110 transition-transform">
        {icon}
      </div>
      <h3 className="text-2xl font-headline font-bold mb-4">{title}</h3>
      <p className="text-on-surface-variant leading-relaxed">{description}</p>
    </div>
  );
}

function WorkflowStep({ number, icon, title, description, accent = false }: { number: string, icon: React.ReactNode, title: string, description: string, accent?: boolean }) {
  return (
    <div className={`rounded-xl p-8 flex flex-col justify-between h-[400px] transition-all duration-500 ${accent ? 'humanizer-gradient text-white shadow-xl shadow-primary/20' : 'bg-surface-container-low hover:bg-surface-container-lowest border border-outline/5'}`}>
      <div>
        <div className={`w-12 h-12 rounded-lg flex items-center justify-center mb-6 ${accent ? 'bg-white/20 backdrop-blur-md' : 'bg-primary/10'}`}>
          {icon}
        </div>
        <h3 className="text-2xl font-headline font-bold mb-4">{title}</h3>
        <p className={accent ? 'text-blue-100' : 'text-on-surface-variant'}>{description}</p>
      </div>
      <div className={`text-6xl font-headline font-black self-end ${accent ? 'text-white/10' : 'text-outline/10'}`}>{number}</div>
    </div>
  );
}

function DeepDiveItem({ icon, title, description }: { icon: React.ReactNode, title: string, description: string }) {
  return (
    <div className="flex gap-6">
      <div className="shrink-0">{icon}</div>
      <div>
        <h4 className="text-xl font-bold mb-2">{title}</h4>
        <p className="text-on-surface-variant">{description}</p>
      </div>
    </div>
  );
}
