<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Luxe Tribe Discovery Capture Form | Trips & Ships</title>
    <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@1,400;1,600&family=Montserrat:wght@400;500;600&family=Playfair+Display:wght@600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --navy-dark: #232c4c;
            --navy-med: #274472;
            --blue-sky: #5290c9;
            --blue-tint: #e7f3f5;
            --border: #e0e4ef;
            --white: #ffffff;
            --bg: #f5f7fa;
            --accent: #5290c9;
        }

        * { box-sizing: border-box; -webkit-print-color-adjust: exact; }
        body { 
            font-family: 'Montserrat', sans-serif; 
            background: var(--bg); 
            color: var(--navy-med); 
            margin: 0; 
            padding-bottom: 100px;
            line-height: 1.6;
        }

        /* Header Styles */
        header {
            background: var(--navy-dark);
            color: var(--white);
            text-align: center;
            padding: 40px 20px;
            border-bottom: 4px solid var(--blue-sky);
        }
        .est { font-size: 0.8rem; letter-spacing: 2px; opacity: 0.8; }
        .brand-name { font-family: 'Playfair Display', serif; font-size: 2.8rem; margin: 10px 0 5px; }
        .subtitle { font-size: 1rem; letter-spacing: 4px; text-transform: uppercase; margin-bottom: 20px; }
        .form-title { font-family: 'Playfair Display', serif; font-size: 1.8rem; color: var(--blue-sky); margin: 0; }
        .tagline { font-family: 'Cormorant Garamond', serif; font-style: italic; font-size: 1.2rem; margin-top: 5px; opacity: 0.9; }

        /* Layout */
        .container { max-width: 1100px; margin: 0 auto; padding: 20px; }
        .section-card { background: var(--white); border-radius: 12px; padding: 30px; margin-bottom: 25px; border: 1px solid var(--border); box-shadow: 0 4px 6px rgba(0,0,0,0.02); }
        h2 { font-family: 'Playfair Display', serif; color: var(--navy-dark); border-bottom: 2px solid var(--blue-tint); padding-bottom: 10px; margin-top: 0; }

        /* Trip Type Pills */
        .type-pills { display: flex; flex-wrap: wrap; justify-content: center; gap: 10px; margin: 30px 0; }
        .pill { 
            padding: 10px 20px; border-radius: 50px; border: 1.5px solid var(--blue-sky); 
            background: var(--white); cursor: pointer; font-weight: 500; transition: 0.2s;
        }
        .pill:hover { background: var(--blue-tint); }
        .pill.active { background: var(--navy-dark); color: white; border-color: var(--navy-dark); }

        /* Grid System */
        .row { display: flex; gap: 20px; margin-bottom: 20px; }
        .col { flex: 1; display: flex; flex-direction: column; }
        label { font-weight: 600; font-size: 0.85rem; margin-bottom: 8px; text-transform: uppercase; color: var(--navy-dark); }
        input, select, textarea { 
            padding: 12px; border: 1.5px solid var(--border); border-radius: 6px; 
            font-family: 'Montserrat', sans-serif; font-size: 1rem; background: var(--white);
        }
        input:focus, textarea:focus { outline: none; border-color: var(--blue-sky); background: var(--blue-tint); }

        /* Chips */
        .chip-group { display: flex; flex-wrap: wrap; gap: 8px; margin-top: 5px; }
        .chip { 
            padding: 6px 14px; border-radius: 20px; background: var(--blue-tint); border: 1px solid transparent;
            font-size: 0.9rem; cursor: pointer; transition: 0.2s;
        }
        .chip.selected { background: var(--blue-sky); color: white; }
        .chip.dashed { border: 1px dashed var(--blue-sky); background: transparent; }

        /* Supplier Cards */
        .supplier-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(210px, 1fr)); gap: 15px; margin-top: 15px; }
        .supplier-card { 
            background: var(--white); border: 1.5px solid var(--border); padding: 15px; border-radius: 8px; 
            cursor: pointer; transition: 0.2s; text-align: center;
        }
        .supplier-card:hover { border-color: var(--blue-sky); box-shadow: 0 4px 12px rgba(82, 144, 201, 0.15); }
        .supplier-card.active { border-color: var(--navy-dark); background: var(--blue-tint); }
        .supplier-card h4 { margin: 0; color: var(--navy-dark); font-size: 1.1rem; }
        .supplier-card p { font-family: 'Cormorant Garamond', serif; font-style: italic; margin: 5px 0 0; font-size: 0.95rem; }

        /* Supplier Panel */
        .supplier-panel { 
            grid-column: 1 / -1; background: var(--white); border: 2px solid var(--navy-dark); 
            border-radius: 12px; padding: 25px; margin-top: 10px; position: relative;
        }
        .panel-header { display: flex; justify-content: space-between; align-items: center; margin-bottom: 20px; }
        .panel-title { font-family: 'Playfair Display', serif; font-size: 2rem; margin: 0; }
        .back-btn { background: none; border: none; color: var(--blue-sky); cursor: pointer; font-weight: 600; font-size: 1rem; }
        .supplier-desc { font-family: 'Cormorant Garamond', serif; font-style: italic; font-size: 1.25rem; color: #444; border-left: 3px solid var(--blue-sky); padding-left: 20px; margin: 20px 0; }

        /* Tiers */
        .tier-block { margin-bottom: 10px; }
        .tier-header { 
            background: var(--blue-tint); padding: 12px 20px; border-radius: 6px; cursor: pointer;
            display: flex; justify-content: space-between; align-items: center; font-weight: 600;
        }
        .tier-header.open { background: var(--navy-dark); color: white; }
        .tier-content { padding: 15px 0; }

        /* Sub-type Tabs */
        .sub-tabs { display: flex; justify-content: center; gap: 8px; margin-bottom: 25px; }
        .tab { padding: 8px 16px; border-radius: 4px; border: 1px solid var(--border); background: #eee; cursor: pointer; font-size: 0.85rem; }
        .tab.active { background: var(--blue-sky); color: white; border-color: var(--blue-sky); }

        /* Progress Bar */
        #progressContainer { position: sticky; top: 0; z-index: 100; background: var(--bg); padding: 10px 0; display: none; }
        .progress-bg { background: var(--border); height: 8px; border-radius: 4px; width: 100%; overflow: hidden; }
        .progress-fill { background: var(--blue-sky); height: 100%; width: 0%; transition: 0.4s; }

        /* Counters */
        .counter-box { display: flex; align-items: center; gap: 15px; background: var(--blue-tint); padding: 10px; border-radius: 6px; width: fit-content; }
        .counter-btn { width: 32px; height: 32px; border-radius: 50%; border: none; background: var(--navy-dark); color: white; cursor: pointer; font-size: 1.2rem; }

        /* Action Bar */
        .action-bar { 
            position: fixed; bottom: 0; left: 0; right: 0; background: var(--navy-dark); 
            padding: 15px 20px; display: flex; justify-content: center; gap: 20px; align-items: center;
            box-shadow: 0 -4px 10px rgba(0,0,0,0.2);
        }
        .btn-primary { background: var(--blue-sky); color: white; border: none; padding: 12px 25px; border-radius: 6px; font-weight: 600; cursor: pointer; }
        .btn-start-over { color: #ff6b6b; text-decoration: none; font-size: 0.9rem; font-weight: 600; }

        /* Toasts & Modals */
        #toast { 
            position: fixed; bottom: 80px; right: 20px; background: #333; color: white; 
            padding: 12px 24px; border-radius: 4px; opacity: 0; transition: 0.3s; pointer-events: none;
        }
        .modal-overlay { 
            position: fixed; inset: 0; background: rgba(0,0,0,0.6); display: none; 
            align-items: center; justify-content: center; z-index: 1000; 
        }
        .modal { background: white; padding: 30px; border-radius: 12px; width: 400px; text-align: center; }

        @media print {
            .type-pills, .action-bar, .sub-tabs, .back-btn, #progressContainer, .counter-btn { display: none !important; }
            body { background: white; padding: 0; }
            .section-card { border: none; box-shadow: none; padding: 10px 0; }
            header { background: white !important; color: black !important; border-bottom: 2px solid #000; }
            .brand-name, .form-title { color: black !important; }
        }
    </style>
</head>
<body>

<header>
    <div class="est">EST 1995</div>
    <div class="brand-name">TRIPS & SHIPS</div>
    <div class="subtitle">Luxury Travel</div>
    <h1 class="form-title">Luxe Tribe Discovery Capture Form</h1>
    <div class="tagline">Curated Escapes</div>
</header>

<div class="container">
    <div class="type-pills" id="typePills">
        </div>

    <div id="progressContainer">
        <div class="progress-bg"><div class="progress-fill" id="progressBar"></div></div>
    </div>

    <div id="formArea">
        </div>
</div>

<div class="action-bar" id="actionBar" style="display: none;">
    <button class="btn-primary" onclick="copySummary()">Copy Discovery Summary</button>
    <button class="btn-primary" onclick="generateFollowUp()">Draft Follow-Up Message</button>
    <button class="btn-primary" onclick="window.print()">Print / Save as PDF</button>
    <a href="#" class="btn-start-over" onclick="confirmReset(event)">Start Over</a>
</div>

<div id="toast">Summary Copied to Clipboard!</div>

<div class="modal-overlay" id="resetModal">
    <div class="modal">
        <h3>Start Over?</h3>
        <p>This will clear all current form data. This action cannot be undone.</p>
        <div style="display: flex; gap: 10px; justify-content: center; margin-top: 20px;">
            <button class="pill" onclick="closeModal()">Cancel</button>
            <button class="pill active" onclick="resetForm()" style="background: #ff6b6b; border-color: #ff6b6b;">Yes, Clear All</button>
        </div>
    </div>
</div>

<script>
    // --- STATE MANAGEMENT ---
    let ST = {
        tripType: null,
        activeSub: null,
        selectedSupplier: null,
        fields: {},
        chips: {},
        addonChips: {},
        destSel: {},
        adults: 1,
        children: []
    };

    const TRIP_TYPES = [
        "Cruising", "Guided Tours", "Rail", "Theme Park", "All-Inclusive", 
        "Resorts & Hotels", "Honeymoon & Weddings", "Adventure/Active", 
        "Safari", "Wellness Retreat", "Group Travel", "Custom/Independent"
    ];

    const SUPPLIER_DATA = {
        "Cruising": {
            tabs: ["Ocean", "River", "Expedition", "Yacht / Small Ship"],
            pricing: "Ultra-Luxury $10,000+/pp | Luxury $5,000–$10,000/pp | Premium $2,500–$5,000/pp | Mass Market $500–$2,500/pp",
            suppliers: {
                "Ocean": [
                    { tier: "ULTRA-LUXE", name: "A&K x Crystal", desc: "Worldwide ultra-luxe sailing.", dests: ["Worldwide"] },
                    { tier: "ULTRA-LUXE", name: "Regent Seven Seas", desc: "Every luxury included.", dests: ["Worldwide"] },
                    { tier: "PREMIUM", name: "Disney Cruise Line", desc: "Magic at sea.", addons: "Disney Cruise Line", dests: ["Caribbean", "Bahamas", "Europe", "Alaska", "Worldwide"] },
                    { tier: "PREMIUM", name: "Virgin Voyages", desc: "Adult-only modern luxury.", addons: "Virgin Voyages", dests: ["Caribbean", "Mediterranean", "Transatlantic"] }
                ],
                "River": [
                    { tier: "ULTRA-LUXE", name: "Uniworld", desc: "Boutique river cruises.", dests: ["Europe", "Mekong", "Nile", "Ganges", "India"] },
                    { tier: "LUXURY", name: "Tauck", desc: "Guided excellence.", dests: ["Europe", "Nile"] }
                ]
            }
        },
        "Theme Park": {
            tabs: ["Disney", "Universal", "Other Parks"],
            pricing: "Standard $1,500–$4,000 | Luxury $6,000–$15,000+ (VIP/Suites)",
            suppliers: {
                "Disney": [
                    { name: "Walt Disney World", desc: "Orlando, Florida", addons: "Walt Disney World", dests: ["Magic Kingdom", "Epcot", "Hollywood Studios", "Animal Kingdom"] },
                    { name: "Aulani", desc: "Ko Olina, Hawaii", addons: "Aulani", dests: ["Ko Olina, Hawaii"] }
                ]
            }
        }
    };

    const CHIP_DATA = {
        comms: ["Call", "Text", "Email", "Instagram", "Facebook", "Other"],
        source: ["Social Media", "Referral", "Google Search", "Repeat Client", "Travel Fair/Event", "Facebook Group", "Other"],
        status: ["Hot Lead", "Warm Lead", "Cold Lead", "Active Planning", "Booked", "Follow-Up Needed", "Not a Fit"],
        insurance: ["Yes: Link Only", "Yes: Quote", "Yes: Supplier Package", "Not Interested", "Undecided", "No: Denied"],
        budget: ["Under $2,500", "$2,500–$5,000", "$5,000–$10,000", "$10,000–$20,000", "$20,000–$50,000", "$50,000+", "Flexible", "Not Sure"],
        addons: {
            "Virgin Voyages": ["Bar Tab Credit", "Extra Eateries", "Spa Package", "Shore Things", "Pre-Voyage Hotel", "Flights"],
            "Walt Disney World": ["Memory Maker", "Genie+", "Dining Plan", "Park Hopper", "VIP Tour", "Character Dining"],
            "Default": ["Flights", "Travel Insurance", "Pre-Trip Hotel", "Post-Trip Hotel", "Airport Transfer"]
        }
    };

    // --- INITIALIZATION ---
    window.onload = () => {
        const pillContainer = document.getElementById('typePills');
        TRIP_TYPES.forEach(type => {
            const btn = document.createElement('button');
            btn.className = 'pill';
            btn.innerText = type;
            btn.onclick = () => selectTripType(type);
            pillContainer.appendChild(btn);
        });
    };

    function selectTripType(type) {
        ST.tripType = type;
        ST.activeSub = (SUPPLIER_DATA[type] && SUPPLIER_DATA[type].tabs) ? SUPPLIER_DATA[type].tabs[0] : null;
        ST.selectedSupplier = null;
        
        document.querySelectorAll('#typePills .pill').forEach(p => {
            p.classList.toggle('active', p.innerText === type);
        });
        
        document.getElementById('actionBar').style.display = 'flex';
        document.getElementById('progressContainer').style.display = 'block';
        
        renderForm();
        updateProgress();
    }

    // --- RENDERING ---
    function renderForm() {
        const area = document.getElementById('formArea');
        let html = '';

        // Supplier Section
        if (!["Group Travel", "Custom/Independent"].includes(ST.tripType)) {
            html += `<div class="section-card">
                <h2>Supplier Selection</h2>
                ${renderSubTabs()}
                ${renderPricingReference()}
                <div class="supplier-grid" id="supplierGrid">
                    ${renderSuppliers()}
                </div>
                <div id="panelSlot"></div>
            </div>`;
        } else {
            html += renderSpecialTripFields();
        }

        // Standard Sections
        html += renderContactSection();
        html += renderTripBasics();
        html += renderPartyDetails();
        html += renderPreferences();
        html += renderBudgetSection();
        html += renderNotesSection();

        area.innerHTML = html;
        restoreFieldValues();
    }

    function renderPricingReference() {
        const data = SUPPLIER_DATA[ST.tripType];
        if (!data || !data.pricing) return '';
        return `<details style="margin-bottom:20px; color: var(--navy-med); font-size: 0.9rem;">
            <summary style="cursor:pointer; font-weight:600;">View Pricing Benchmarks</summary>
            <p style="padding:10px; background:var(--blue-tint); border-radius:4px;">${data.pricing}</p>
        </details>`;
    }

    function renderSubTabs() {
        const data = SUPPLIER_DATA[ST.tripType];
        if (!data || !data.tabs) return '';
        return `<div class="sub-tabs">
            ${data.tabs.map(t => `<button class="tab ${ST.activeSub === t ? 'active' : ''}" onclick="selectSubTab('${t}')">${t}</button>`).join('')}
        </div>`;
    }

    function selectSubTab(tab) {
        ST.activeSub = tab;
        ST.selectedSupplier = null;
        renderForm();
    }

    function renderSuppliers() {
        const data = SUPPLIER_DATA[ST.tripType];
        if (!data || !ST.activeSub || !data.suppliers[ST.activeSub]) return '<p>No specific suppliers listed for this subtype.</p>';
        
        return data.suppliers[ST.activeSub].map(s => `
            <div class="supplier-card ${ST.selectedSupplier === s.name ? 'active' : ''}" onclick="toggleSupplier('${s.name}')">
                <h4>${s.name}</h4>
                <p>${s.tier || ''}</p>
            </div>
        `).join('');
    }

    function toggleSupplier(name) {
        if (ST.selectedSupplier === name) {
            ST.selectedSupplier = null;
        } else {
            ST.selectedSupplier = name;
        }
        renderForm();
        if (ST.selectedSupplier) {
            document.getElementById('panelSlot').innerHTML = renderSupplierPanel(name);
            document.getElementById('panelSlot').scrollIntoView({ behavior: 'smooth', block: 'center' });
        }
    }

    function renderSupplierPanel(name) {
        const s = SUPPLIER_DATA[ST.tripType].suppliers[ST.activeSub].find(x => x.name === name);
        const addons = CHIP_DATA.addons[s.addons] || CHIP_DATA.addons.Default;

        return `
            <div class="supplier-panel">
                <div class="panel-header">
                    <h3 class="panel-title">${s.name}</h3>
                    <button class="back-btn" onclick="toggleSupplier('${name}')">← Back to Grid</button>
                </div>
                <div class="supplier-desc">${s.desc}</div>
                
                <label>Destinations</label>
                <div class="chip-group">
                    ${s.dests.map(d => `<div class="chip ${ST.destSel[name]?.includes(d) ? 'selected' : ''}" onclick="toggleDest('${name}', '${d}')">${d}</div>`).join('')}
                    <div class="chip dashed">Undecided</div>
                </div>

                <div class="row" style="margin-top:20px;">
                    <div class="col">
                        <label>Add-Ons & Extras</label>
                        <div class="chip-group">
                            ${addons.map(a => `<div class="chip ${ST.addonChips[name]?.includes(a) ? 'selected' : ''}" onclick="toggleAddon('${name}', '${a}')">${a}</div>`).join('')}
                        </div>
                    </div>
                </div>

                <div class="row">
                    <div class="col">
                        <label>Cabin / Suite Interest</label>
                        <textarea rows="2" oninput="saveField('${name}_cabin', this.value)">${ST.fields[name + '_cabin'] || ''}</textarea>
                    </div>
                </div>
            </div>
        `;
    }

    function renderContactSection() {
        return `
            <div class="section-card">
                <h2>Contact & Lead Info</h2>
                <div class="row">
                    <div class="col"><label>First Name</label><input type="text" oninput="saveField('fname', this.value)" value="${ST.fields.fname || ''}"></div>
                    <div class="col"><label>Last Name</label><input type="text" oninput="saveField('lname', this.value)" value="${ST.fields.lname || ''}"></div>
                </div>
                <div class="row">
                    <div class="col"><label>Email</label><input type="email" oninput="saveField('email', this.value)" value="${ST.fields.email || ''}"></div>
                    <div class="col"><label>Phone</label><input type="tel" oninput="saveField('phone', this.value)" value="${ST.fields.phone || ''}"></div>
                </div>
                <label>Lead Status</label>
                <div class="chip-group">
                    ${CHIP_DATA.status.map(s => `<div class="chip ${ST.chips.status === s ? 'selected' : ''}" onclick="selectChip('status', '${s}')">${s}</div>`).join('')}
                </div>
            </div>
        `;
    }

    function renderPartyDetails() {
        let childInputs = '';
        ST.children.forEach((c, idx) => {
            childInputs += `<input type="number" placeholder="Age" style="width:60px" oninput="ST.children[${idx}].age=this.value" value="${c.age}">`;
        });

        return `
            <div class="section-card">
                <h2>Party Details</h2>
                <div class="row">
                    <div class="col">
                        <label>Adults</label>
                        <div class="counter-box">
                            <button class="counter-btn" onclick="updateCounter('adults', -1)">-</button>
                            <span style="font-weight:600">${ST.adults}</span>
                            <button class="counter-btn" onclick="updateCounter('adults', 1)">+</button>
                        </div>
                    </div>
                    <div class="col">
                        <label>Children</label>
                        <div class="counter-box">
                            <button class="counter-btn" onclick="updateCounter('children', -1)">-</button>
                            <span style="font-weight:600">${ST.children.length}</span>
                            <button class="counter-btn" onclick="updateCounter('children', 1)">+</button>
                        </div>
                        <div class="chip-group" style="margin-top:10px">${childInputs}</div>
                    </div>
                </div>
            </div>
        `;
    }

    function renderTripBasics() {
        return `<div class="section-card">
            <h2>Trip Basics</h2>
            <div class="row">
                <div class="col"><label>Departure Month/Year</label><input type="text" placeholder="e.g. June 2026" oninput="saveField('dep', this.value)" value="${ST.fields.dep || ''}"></div>
                <div class="col"><label>Return Month/Year</label><input type="text" oninput="saveField('ret', this.value)" value="${ST.fields.ret || ''}"></div>
            </div>
        </div>`;
    }

    function renderPreferences() {
        return `<div class="section-card">
            <h2>Preferences</h2>
            <label>Occasion</label>
            <div class="chip-group">
                ${["Honeymoon", "Anniversary", "Birthday", "Retirement", "Bucket List", "None"].map(o => `<div class="chip ${ST.chips.occasion === o ? 'selected' : ''}" onclick="selectChip('occasion', '${o}')">${o}</div>`).join('')}
            </div>
        </div>`;
    }

    function renderBudgetSection() {
        return `<div class="section-card">
            <h2>Budget</h2>
            <label>Total All-In Budget</label>
            <div class="chip-group">
                ${CHIP_DATA.budget.map(b => `<div class="chip ${ST.chips.budget === b ? 'selected' : ''}" onclick="selectChip('budget', '${b}')">${b}</div>`).join('')}
            </div>
        </div>`;
    }

    function renderNotesSection() {
        return `<div class="section-card">
            <h2>Notes & Follow-Up</h2>
            <div class="col">
                <label>General Notes</label>
                <textarea rows="6" oninput="saveField('notes', this.value)">${ST.fields.notes || ''}</textarea>
            </div>
            <div class="row" style="margin-top:20px;">
                <div class="col">
                    <label>Priority Level</label>
                    <div class="chip-group">
                        ${["Hot", "High", "Standard", "Low"].map(p => `<div class="chip ${ST.chips.priority === p ? 'selected' : ''}" onclick="selectChip('priority', '${p}')">${p}</div>`).join('')}
                    </div>
                </div>
            </div>
        </div>`;
    }

    function renderSpecialTripFields() {
        return `<div class="section-card">
            <h2>${ST.tripType} Details</h2>
            <div class="col">
                <label>Destination(s) in Mind</label>
                <input type="text" oninput="saveField('spec_dest', this.value)" value="${ST.fields.spec_dest || ''}">
                <label style="margin-top:15px;">Additional Context</label>
                <textarea rows="4" oninput="saveField('spec_notes', this.value)">${ST.fields.spec_notes || ''}</textarea>
            </div>
        </div>`;
    }

    // --- LOGIC ---
    function saveField(key, val) { 
        ST.fields[key] = val; 
        updateProgress();
    }
    
    function selectChip(group, val) { 
        ST.chips[group] = val; 
        renderForm(); 
        updateProgress();
    }

    function toggleAddon(sname, val) {
        if (!ST.addonChips[sname]) ST.addonChips[sname] = [];
        const idx = ST.addonChips[sname].indexOf(val);
        if (idx > -1) ST.addonChips[sname].splice(idx, 1);
        else ST.addonChips[sname].push(val);
        renderForm();
    }

    function toggleDest(sname, val) {
        if (!ST.destSel[sname]) ST.destSel[sname] = [];
        const idx = ST.destSel[sname].indexOf(val);
        if (idx > -1) ST.destSel[sname].splice(idx, 1);
        else ST.destSel[sname].push(val);
        renderForm();
    }

    function updateCounter(type, change) {
        if (type === 'adults') ST.adults = Math.max(0, ST.adults + change);
        else {
            if (change > 0) ST.children.push({age: ''});
            else ST.children.pop();
        }
        renderForm();
        updateProgress();
    }

    function updateProgress() {
        let score = 0;
        if (ST.fields.fname && ST.fields.email) score += 1;
        if (ST.fields.dep) score += 1;
        if (ST.adults > 0) score += 1;
        if (ST.chips.budget) score += 1;
        if (ST.selectedSupplier || ["Group Travel", "Custom/Independent"].includes(ST.tripType)) score += 1;
        if (ST.fields.notes) score += 1;

        const perc = (score / 6) * 100;
        document.getElementById('progressBar').style.width = perc + '%';
    }

    function restoreFieldValues() {
        // Handled by rendering logic using ST object
    }

    // --- ACTIONS ---
    function copySummary() {
        let text = `LUXE TRIBE DISCOVERY SUMMARY\n`;
        text += `Trip Type: ${ST.tripType} (${ST.activeSub || 'N/A'})\n`;
        text += `Client: ${ST.fields.fname || ''} ${ST.fields.lname || ''}\n`;
        text += `Contact: ${ST.fields.email || ''} | ${ST.fields.phone || ''}\n`;
        text += `Dates: ${ST.fields.dep || 'TBD'} to ${ST.fields.ret || 'TBD'}\n`;
        text += `Party: ${ST.adults} Adults, ${ST.children.length} Children\n`;
        if (ST.selectedSupplier) text += `Selected Supplier: ${ST.selectedSupplier}\n`;
        text += `Budget Range: ${ST.chips.budget || 'Not Selected'}\n`;
        text += `Notes: ${ST.fields.notes || 'None'}\n`;

        navigator.clipboard.writeText(text);
        const toast = document.getElementById('toast');
        toast.style.opacity = '1';
        setTimeout(() => toast.style.opacity = '0', 2000);
    }

    function generateFollowUp() {
        const name = ST.fields.fname || 'there';
        const trip = ST.tripType;
        const occasion = ST.chips.occasion && ST.chips.occasion !== 'None' ? ` for your ${ST.chips.occasion}` : '';
        
        const msg = `Hi ${name}! It was wonderful speaking with you about your upcoming ${trip}${occasion}. I'm starting to look into some incredible options for your ${ST.fields.dep || 'trip'} and will have a proposal ready for you soon.`;
        
        const win = window.open("", "_blank");
        win.document.write(`<pre style="font-family:sans-serif; padding:20px;">${msg}</pre>`);
    }

    function confirmReset(e) {
        e.preventDefault();
        document.getElementById('resetModal').style.display = 'flex';
    }

    function closeModal() {
        document.getElementById('resetModal').style.display = 'none';
    }

    function resetForm() {
        ST = { tripType: null, activeSub: null, selectedSupplier: null, fields: {}, chips: {}, addonChips: {}, destSel: {}, adults: 1, children: [] };
        document.getElementById('formArea').innerHTML = '';
        document.getElementById('actionBar').style.display = 'none';
        document.getElementById('progressContainer').style.display = 'none';
        document.querySelectorAll('.pill').forEach(p => p.classList.remove('active'));
        closeModal();
    }

    // --- KEYBOARD SHORTCUTS ---
    window.onkeydown = (e) => {
        if ((e.ctrlKey || e.metaKey) && e.shiftKey && e.key === 'C') {
            copySummary();
        }
        if (e.key === 'Escape') {
            closeModal();
        }
    };
</script>

</body>
</html>
