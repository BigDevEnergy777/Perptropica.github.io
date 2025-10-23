# Perptropica.github.io
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>PerpTropica — Fee-Free Perp DEX</title>
  <!-- React and ReactDOM via CDN -->
  <script crossorigin src="https://unpkg.com/react@18/umd/react.production.min.js"></script>
  <script crossorigin src="https://unpkg.com/react-dom@18/umd/react-dom.production.min.js"></script>
  <!-- React Router DOM via CDN -->
  <script crossorigin src="https://unpkg.com/react-router-dom@6/umd/react-router-dom.production.min.js"></script>
  <!-- Inter font -->
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;700;800&display=swap" rel="stylesheet">
  <style>
    body, html { margin:0; padding:0; font-family: 'Inter', sans-serif; color:#e6f7ff; background:#00121a; }
    a { color:#6ee7b7; text-decoration:none; }
    button { cursor:pointer; }
  </style>
</head>
<body>
  <div id="root"></div>

  <script type="text/javascript">
    const { BrowserRouter, Routes, Route, Link, useNavigate } = ReactRouterDOM;

    // Styles
    const pageBackground = {
      minHeight: '100vh',
      margin: 0,
      color: '#e6f7ff',
      background: 'linear-gradient(180deg, #00121a 0%, #032a36 35%, #063b52 60%, #0b6b7a 100%)',
      backgroundAttachment: 'fixed',
      fontFamily: "Inter, ui-sans-serif, system-ui, -apple-system, 'Segoe UI', Roboto, 'Helvetica Neue', Arial",
    };
    const container = { maxWidth: 1200, margin: '0 auto', padding: '120px 20px 80px' };
    const navLink = { color: 'rgba(230,247,255,0.95)', textDecoration: 'none', padding: '6px 10px', borderRadius: 8, fontSize: 14 };
    const smallCard = { padding: '8px 12px', borderRadius: 10, background: 'rgba(255,255,255,0.03)', color: '#e6f7ff', textDecoration: 'none', fontWeight: 700 };

    function Navbar() {
      return (
        React.createElement('div', { style: {position: 'fixed', top:0, left:0, right:0, zIndex:60, padding:'12px 20px', borderBottom:'1px solid rgba(255,255,255,0.04)', background:'linear-gradient(180deg, rgba(0,0,0,0.38), transparent)'} },
          React.createElement('div', { style:{maxWidth:1200, margin:'0 auto', display:'flex', alignItems:'center', justifyContent:'space-between'} },
            React.createElement(Link, { to:'/', style:{color:'#6ee7b7', fontWeight:800, fontSize:20, textDecoration:'none'} }, '🌴 PerpTropica'),
            React.createElement('nav', { style:{display:'flex', gap:12, alignItems:'center'} },
              React.createElement(Link, { to:'/', style:navLink }, 'Home'),
              React.createElement(Link, { to:'/zerofees', style:navLink }, 'Zero Fees'),
              React.createElement(Link, { to:'/token', style:navLink }, 'Token'),
              React.createElement(Link, { to:'/chart', style:navLink }, 'Live Chart'),
              React.createElement(Link, { to:'/about', style:navLink }, 'About'),
              React.createElement('a', { href:'https://x.com/PerpTropica', target:'_blank', rel:'noreferrer', style:{...navLink, opacity:0.95} }, 'Twitter')
            )
          )
        )
      );
    }

    function Footer() {
      return (
        React.createElement('footer', { style:{padding:'40px 20px', textAlign:'center', borderTop:'1px solid rgba(255,255,255,0.03)'} },
          React.createElement('div', { style:{maxWidth:1200, margin:'0 auto', color:'rgba(230,247,255,0.6)'} },
            React.createElement('div', { style:{marginBottom:8} }, React.createElement(Link, { to:'/' }, '🌴 Back to Home')),
            React.createElement('div', null, `© ${new Date().getFullYear()} PerpTropica — Fee-Free Perp DEX`)
          )
        )
      );
    }

    function ComingSoonButton({ children }) {
      return React.createElement('button', {
        onClick: e=>{ e.preventDefault(); alert('Coming soon — wallet connection will be live in a future release.'); },
        style:{padding:'10px 16px', borderRadius:12, border:'none', fontWeight:700, background:'linear-gradient(90deg,#6ee7b7,#60a5fa)', color:'#012', boxShadow:'0 8px 30px rgba(96,165,250,0.12)'}
      }, children);
    }

    function VisualPlaceholder({ label }) {
      return (
        React.createElement('div', { style:{marginTop:20, borderRadius:12, overflow:'hidden', boxShadow:'0 20px 60px rgba(2,6,23,0.6)'} },
          React.createElement('div', { style:{background:'#00121a', padding:22} },
            React.createElement('div', { style:{color:'#6ee7b7', fontWeight:800, fontSize:16} }, label),
            React.createElement('img', { src:`https://placehold.co/900x300?text=${encodeURIComponent(label)}`, alt:label, style:{width:'100%', marginTop:12, borderRadius:8} })
          )
        )
      );
    }

    // Pages: Home, ZeroFees, Token, Chart, About
    function Home() {
      return React.createElement('main', { style:pageBackground },
        React.createElement('div', { style:container },
          React.createElement('section', { style:{display:'grid', gridTemplateColumns:'1fr 1fr', gap:36, alignItems:'start'} },
            React.createElement('div', null,
              React.createElement('h1', { style:{fontSize:48, margin:0, lineHeight:1.02, color:'white', textShadow:'0 4px 30px rgba(6,182,183,0.12)'} },
                'PerpTropica', React.createElement('br'), React.createElement('span', { style:{color:'#6ee7b7', fontWeight:800} }, 'Trade freely. Live tropically.')
              ),
              React.createElement('div', { style:{marginTop:22} },
                React.createElement(ComingSoonButton, null, 'Connect Wallet (Coming Soon 🌴)'),
                React.createElement(Link, { to:'/chart', style:{padding:'10px 16px', borderRadius:12, background:'rgba(255,255,255,0.04)', color:'#e6f7ff', textDecoration:'none', fontWeight:700, marginLeft:12} }, 'Live Chart')
              ),
              React.createElement('p', { style:{marginTop:16, lineHeight:1.8} }, 'PerpTropica is the world’s first fee-free perpetual DEX for meme coins and derivatives. $TROPIC funds free trades, airdrops reward active traders, and the platform merges DeFi with tropical vibes.'),
              React.createElement(VisualPlaceholder, { label:'Platform Snapshot' })
            ),
            React.createElement('div', null,
              React.createElement(VisualPlaceholder, { label:'Ecosystem Diagram (placeholder)' }),
              React.createElement('div', { style:{marginTop:20} },
                React.createElement(Link, { to:'/zerofees', style:smallCard }, 'How Zero Fees Work'),
                React.createElement(Link, { to:'/token', style:{...smallCard, marginLeft:10} }, 'Token Info')
              )
            )
          )
        ),
        React.createElement(Footer, null)
      );
    }

    function ZeroFees() {
      return React.createElement('main', { style:pageBackground },
        React.createElement('div', { style:container },
          React.createElement(Link, { to:'/', style:{color:'#6ee7b7', marginBottom:18, display:'inline-block'} }, '← Back to Home'),
          React.createElement('h2', { style:{fontSize:32} }, 'How Zero Fees Work'),
          React.createElement('p', { style:{marginTop:12, lineHeight:1.8, color:'rgba(230,247,255,0.85)'} },
            'PerpTropica uses $TROPIC to reimburse trade fees via relayers. Weekly airdrops fund fee wallets, allowing traders to execute strategies without paying on-chain fees.'
          ),
          React.createElement(VisualPlaceholder, { label:'Zero Fees Flow (placeholder)' })
        ),
        React.createElement(Footer, null)
      );
    }

    function Token() {
      return React.createElement('main', { style:pageBackground },
        React.createElement('div', { style:container },
          React.createElement(Link, { to:'/', style:{color:'#6ee7b7', marginBottom:18, display:'inline-block'} }, '← Back to Home'),
          React.createElement('h2', { style:{fontSize:32} }, 'Token — $TROPIC'),
          React.createElement('p', { style:{marginTop:12, lineHeight:1.8, color:'rgba(230,247,255,0.85)'} },
            '$TROPIC powers fee reimbursement and governance. Early adopters earn airdrops, and staking and partnerships create extra utility.'
          ),
          React.createElement(VisualPlaceholder, { label:'Tokenomics Chart (placeholder)' })
        ),
        React.createElement(Footer, null)
      );
    }

    function Chart() {
      return React.createElement('main', { style:pageBackground },
        React.createElement('div', { style:container },
          React.createElement(Link, { to:'/', style:{color:'#6ee7b7', marginBottom:18, display:'inline-block'} }, '← Back to Home'),
          React.createElement('h2', { style:{fontSize:32} }, 'Live Chart'),
          React.createElement('iframe', {
            title:'PerpTropica chart',
            src:'https://dexscreener.com/solana/6jRuRhjtXgMAF1Z4nQuu1oaCxNu2wLiqVt7L64Xpump',
            width:'100%',
            height:650,
            style:{border:0, display:'block', marginTop:18, borderRadius:12, boxShadow:'0 20px 60px rgba(2,6,23,0.6)'}
          }),
          React.createElement('p', { style:{marginTop:18, lineHeight:1.8, color:'rgba(230,247,255,0.85)'} }, 'Live charts help traders visualize price action, liquidity, and volume in real-time.')
        ),
        React.createElement(Footer, null)
      );
    }

    function About() {
      return React.createElement('main', { style:pageBackground },
        React.createElement('div', { style:container },
          React.createElement(Link, { to:'/', style:{color:'#6ee7b7', marginBottom:18, display:'inline-block'} }, '← Back to Home'),
          React.createElement('h2', { style:{fontSize:32} }, 'About PerpTropica'),
          React.createElement('p', { style:{marginTop:12, lineHeight:1.8, color:'rgba(230,247,255,0.85)'} },
            'PerpTropica is a community-first, fee-free DEX for meme coins and perpetual trading. It is permissionless, transparent, and governed by $TROPIC holders.'
          ),
          React.createElement(VisualPlaceholder, { label:'Team & Community (placeholder)' })
        ),
        React.createElement(Footer, null)
      );
    }

    function App() {
      return React.createElement(BrowserRouter, null,
        React.createElement(Navbar, null),
        React.createElement(Routes, null,
          React.createElement(Route, { path:'/', element:React.createElement(Home, null) }),
          React.createElement(Route, { path:'/zerofees', element:React.createElement(ZeroFees, null) }),
          React.createElement(Route, { path:'/token', element:React.createElement(Token, null) }),
          React.createElement(Route, { path:'/chart', element:React.createElement(Chart, null) }),
          React.createElement(Route, { path:'/about', element:React.createElement(About, null) }),
          React.createElement(Route, { path:'*', element:React.createElement(Home, null) })
        )
      );
    }

    ReactDOM.createRoot(document.getElementById('root')).render(React.createElement(App));
  </script>
</body>
</html>
