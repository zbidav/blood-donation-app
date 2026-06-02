# Endemic Countries — Tourist Destinations Feature
## Session Summary: 2026-03-28

### Concept
For endemic countries with **partial risk zones** (not entire country), add a list of 
popular tourist destinations with clear ✅ (safe) / ⚠️ (malaria risk) status.
This helps donors who visited these countries recall whether they were in a risk zone.

### Design Decisions
- **Format**: Accordion button (📍) inside the country card, click to expand
- **Languages**: Hebrew + English only (consistent with medical tables)
- **Russian**: Deferred to later phase
- **Data structure**: New `DATA_DESTINATIONS` object, keyed by English country name
- **Rendering**: Modify `renderCountryCard` to add accordion when destinations exist

### Note on India
India has a blanket 12-month deferral in MDA data (no regional breakdown).
We included tourist destinations anyway for informational value, but practically 
anyone flying to India passes through Mumbai/Delhi (low-altitude = risk zone).
David flagged this as slightly odd but wants to keep it for now.

---

## Destination Data (13 Countries)

### 🇵🇪 Peru
Malaria: risk below 2500m, east of Andes (including Iquitos, Puerto Maldonado)

**✅ Safe (no malaria risk):**
| Name | nameHe | reason (he) | reason (en) |
|------|--------|-------------|-------------|
| Lima | לימה | חוף מערבי | West coast |
| Cusco | קוסקו | ~3,400m | ~3,400m altitude |
| Machu Picchu | מאצ'ו פיצ'ו | הרי האנדים | Andes mountains |
| Puno / Lake Titicaca | פונו / אגם טיטיקקה | ~3,800m | ~3,800m altitude |
| Arequipa | ארקיפה | מערב לאנדים | West of Andes |
| Nazca | נסקה | חוף מערבי | West coast |
| Huaraz | וואראס | ~3,050m | ~3,050m altitude |
| Paracas | פרקאס | חוף | Coastal |

**⚠️ Risk (malaria deferral 12 months):**
| Name | nameHe | reason (he) | reason (en) |
|------|--------|-------------|-------------|
| Iquitos | איקיטוס | אגן האמזונס | Amazon basin |
| Puerto Maldonado | פוארטו מלדונדו | אגן האמזונס | Amazon basin |
| Manu National Park | פארק לאומי מאנו | ג'ונגל, אמזונס | Jungle, Amazon |
| Tambopata | טמבופטה | ג'ונגל, אמזונס | Jungle, Amazon |

---

### 🇨🇴 Colombia
Malaria: all areas below 1700m

**✅ Safe:**
| Name | nameHe | reason (he) | reason (en) |
|------|--------|-------------|-------------|
| Bogotá | בוגוטה | ~2,600m | ~2,600m altitude |
| Medellín | מדיין | עירוני, ~1,500m | Urban, ~1,500m |
| Villa de Leyva | וילה דה ליבה | ~2,150m | ~2,150m altitude |
| Salento / Valle de Cocora | סלנטו / עמק קוקורה | ~1,900m | ~1,900m altitude |

**⚠️ Risk:**
| Name | nameHe | reason (he) | reason (en) |
|------|--------|-------------|-------------|
| Cartagena | קרטחנה | חוף, גובה ימה | Coast, sea level |
| Santa Marta / Tayrona | סנטה מרתה / טיירונה | חוף טרופי | Tropical coast |
| Leticia | לטיסיה | אמזונס | Amazon |
| San Andrés | סן אנדרס | קריביים | Caribbean |

---

### 🇧🇷 Brazil
Malaria: states Acre, Amapá, Amazonas, Rondônia, Roraima

**✅ Safe:**
| Name | nameHe | reason (he) | reason (en) |
|------|--------|-------------|-------------|
| Rio de Janeiro | ריו דה ז'ניירו | דרום-מזרח | Southeast |
| São Paulo | סאו פאולו | דרום-מזרח | Southeast |
| Salvador | סלבדור | בהייה, חוף | Bahia, coast |
| Florianópolis | פלוריאנופוליס | דרום | South |
| Iguazu Falls | מפלי איגואסו | דרום | South |

**⚠️ Risk:**
| Name | nameHe | reason (he) | reason (en) |
|------|--------|-------------|-------------|
| Manaus | מנאוס | אמזונס | Amazon |
| Belém | בלם | אגן האמזונס | Amazon basin |

---

### 🇲🇽 Mexico
Malaria: Campeche, Chiapas, southern Chihuahua

**✅ Safe:**
| Name | nameHe | reason (he) | reason (en) |
|------|--------|-------------|-------------|
| Cancún / Riviera Maya | קנקון / ריביירה מאיה | יוקטן | Yucatan |
| Mexico City | מקסיקו סיטי | מרכז, גבוה | Central, high altitude |
| Oaxaca | אואחאקה | מרכז | Central |
| Guadalajara | גוודלחרה | מרכז-מערב | Central-west |
| Puerto Vallarta | פוארטו ויארטה | חוף מערבי | West coast |
| Tulum | טולום | יוקטן | Yucatan |

**⚠️ Risk:**
| Name | nameHe | reason (he) | reason (en) |
|------|--------|-------------|-------------|
| Palenque | פלנקה | צ'יאפס | Chiapas |
| San Cristóbal de las Casas | סן כריסטובל | צ'יאפס | Chiapas |

---

### 🇹🇭 Thailand
Malaria: border provinces with Burma, Cambodia, Malaysia (rural forested areas)

**✅ Safe:**
| Name | nameHe | reason (he) | reason (en) |
|------|--------|-------------|-------------|
| Bangkok | בנגקוק | עירוני | Urban |
| Chiang Mai (city) | צ'יאנג מאי (העיר) | עירוני | Urban |
| Phuket | פוקט | תיירותי | Tourist area |
| Koh Samui / Koh Phangan | קו סמוי / קו פנגן | איים | Islands |
| Krabi / Ao Nang | קראבי / או נאנג | חוף | Coast |
| Pattaya | פטאיה | עירוני-חוף | Urban-coast |

**⚠️ Risk:**
| Name | nameHe | reason (he) | reason (en) |
|------|--------|-------------|-------------|
| Koh Chang | קו צ'אנג | אזור גבול קמבודיה | Cambodia border area |
| Mae Hong Son / Pai | מאה הונג סון / פאי | גבול בורמה, כפרי-מיוער | Burma border, rural-forested |
| Northern border treks | טרקים בצפון לאורך הגבול | כפרי-מיוער | Rural-forested |

---

### 🇰🇭 Cambodia
Malaria: no risk in Phnom Penh, Siem Reap, Angkor Wat

**✅ Safe:**
| Name | nameHe | reason (he) | reason (en) |
|------|--------|-------------|-------------|
| Phnom Penh | פנום פן | עירוני | Urban |
| Siem Reap / Angkor Wat | סיאם ריפ / אנגקור ואט | עירוני-תיירותי | Urban-tourist |
| Sihanoukville / Koh Rong | סיהנוקוויל / קו רונג | חוף | Coast |

**⚠️ Risk:**
| Name | nameHe | reason (he) | reason (en) |
|------|--------|-------------|-------------|
| Mondulkiri | מונדולקירי | כפרי | Rural |
| Ratanakiri | רטנקירי | כפרי-יערות | Rural-forested |

---

### 🇮🇳 India
Malaria: blanket 12-month deferral (no regional breakdown in MDA data)

**✅ Safe (based on general knowledge — not MDA-verified):**
| Name | nameHe | reason (he) | reason (en) |
|------|--------|-------------|-------------|
| Dharamsala / McLeod Ganj | דרמסאלה / מקלאוד גנג' | הרים, >2,000m | Mountains, >2,000m |
| Leh / Ladakh | לה / לדאק | הרים, >3,000m | Mountains, >3,000m |
| Manali | מנאלי | הרים | Mountains |

**⚠️ Risk:**
| Name | nameHe | reason (he) | reason (en) |
|------|--------|-------------|-------------|
| Goa | גואה | חוף טרופי | Tropical coast |
| Kerala | קרלה | דרום, טרופי | South, tropical |
| Rajasthan (partial) | רג'סטאן (חלקי) | מדברי-נמוך | Desert-low |
| Varanasi | ורנאסי | צפון, נמוך | North, low altitude |
| Mumbai / Delhi | מומבאי / דלהי | עירוני אבל נמוך | Urban but low altitude |

---

### 🇻🇳 Vietnam
Malaria: risk in rural areas

**✅ Safe:**
| Name | nameHe | reason (he) | reason (en) |
|------|--------|-------------|-------------|
| Hanoi | האנוי | עירוני | Urban |
| Ho Chi Minh City | הו צ'י מין סיטי | עירוני | Urban |
| Hội An / Đà Nẵng | הוי אן / דה נאנג | עירוני-חוף | Urban-coast |
| Huế | הואה | עירוני | Urban |
| Ha Long Bay | מפרץ הא לונג | תיירותי | Tourist area |
| Nha Trang | ניה טראנג | חוף-תיירותי | Coast-tourist |
| Sapa (town) | סאפה (העיירה) | תיירותי | Tourist area |

**⚠️ Risk:**
| Name | nameHe | reason (he) | reason (en) |
|------|--------|-------------|-------------|
| Central Highlands (rural) | רמת המרכז (כפרי) | כפרי | Rural |
| Rural mountain treks | טרקים כפריים | כפרי | Rural |

---

### 🇮🇩 Indonesia
Malaria: Eastern Indonesia (Maluku, North Maluku, East Nusa Tenggara, Papua, West Papua)

**✅ Safe:**
| Name | nameHe | reason (he) | reason (en) |
|------|--------|-------------|-------------|
| Bali | באלי | מערב | West |
| Jakarta | ג'קרטה | מערב, עירוני | West, urban |
| Yogyakarta | יוגיאקרטה | מערב, ג'אווה | West, Java |
| Lombok | לומבוק | מערב | West |
| Gili Islands | איי גילי | מערב | West |
| Komodo / Flores | קומודו / פלורס | Nusa Tenggara מערבי | West Nusa Tenggara |

**⚠️ Risk:**
| Name | nameHe | reason (he) | reason (en) |
|------|--------|-------------|-------------|
| Raja Ampat | ראג'ה אמפט | פפואה | Papua |
| Jayapura | ג'איאפורה | פפואה | Papua |
| Ambon | אמבון | מלוקו | Maluku |

---

### 🇳🇵 Nepal
Malaria: Sudurpashchim and Karnali provinces below 2000m

**✅ Safe:**
| Name | nameHe | reason (he) | reason (en) |
|------|--------|-------------|-------------|
| Kathmandu | קטמנדו | ~1,400m, עירוני מרכזי | ~1,400m, central urban |
| Pokhara | פוקרה | ~800m, אזור מרכזי | ~800m, central area |
| Everest Base Camp trek | טרק בייס קמפ אוורסט | גובה רב | High altitude |
| Annapurna Circuit | מעגל אנפורנה | גובה רב | High altitude |
| Chitwan National Park | פארק לאומי צ'יטוואן | דרום-מרכז | South-central |

**⚠️ Risk:**
| Name | nameHe | reason (he) | reason (en) |
|------|--------|-------------|-------------|
| Far-West areas (Sudurpashchim) | אזורי Far-West | פרובינציית סיכון | Risk province |

---

### 🇵🇭 Philippines
Malaria: Palawan and Mindanao islands

**✅ Safe:**
| Name | nameHe | reason (he) | reason (en) |
|------|--------|-------------|-------------|
| Manila | מנילה | לוזון, עירוני | Luzon, urban |
| Boracay | בורקאי | ויסאיאס | Visayas |
| Cebu | סבו | ויסאיאס | Visayas |
| Siargao | סיארגאו | חוף-תיירותי | Coast-tourist |
| Bohol | בוהול | ויסאיאס | Visayas |

**⚠️ Risk:**
| Name | nameHe | reason (he) | reason (en) |
|------|--------|-------------|-------------|
| El Nido / Coron | אל נידו / קורון | פלאוואן | Palawan |
| Puerto Princesa | פוארטו פרינססה | פלאוואן | Palawan |
| Davao | דבאו | מינדנאו | Mindanao |

---

### 🇱🇦 Laos
Malaria: southern parts (Attapeu, Champasak, Khammouane, Savannakhet...)

**✅ Safe:**
| Name | nameHe | reason (he) | reason (en) |
|------|--------|-------------|-------------|
| Vientiane | ויינטיאן | בירה, צפון | Capital, north |
| Luang Prabang | לואנג פרבאנג | צפון | North |

**⚠️ Risk:**
| Name | nameHe | reason (he) | reason (en) |
|------|--------|-------------|-------------|
| 4000 Islands | 4000 האיים | Champasak | Champasak |
| Bolaven Plateau | רמת בולאוון | דרום | South |
| Thakhek Loop | לולאת תאקק | Khammouane | Khammouane |

---

### 🇲🇾 Malaysia
Malaria: rural and forested areas

**✅ Safe:**
| Name | nameHe | reason (he) | reason (en) |
|------|--------|-------------|-------------|
| Kuala Lumpur | קואלה לומפור | עירוני | Urban |
| Penang | פננג | עירוני-תיירותי | Urban-tourist |
| Langkawi | לנקאווי | אי תיירותי | Tourist island |
| Malacca | מלקה | עירוני | Urban |

**⚠️ Risk:**
| Name | nameHe | reason (he) | reason (en) |
|------|--------|-------------|-------------|
| Borneo interior (Sarawak/Sabah rural) | פנים בורנאו (סאראוואק/סאבה כפרי) | מיוער | Forested |
| Taman Negara | טאמאן נגרה | יער גשם | Rainforest |

---

### 🇪🇨 Ecuador
Malaria: below 1500m in provinces Cotopaxi, Esmeraldas, Morona Santiago...

**✅ Safe:**
| Name | nameHe | reason (he) | reason (en) |
|------|--------|-------------|-------------|
| Quito | קיטו | ~2,800m | ~2,800m altitude |
| Cuenca | קואנקה | ~2,500m | ~2,500m altitude |
| Galápagos Islands | איי גלפגוס | איים, אין סיכון | Islands, no risk |
| Otavalo | אוטבלו | הרים | Mountains |
| Baños | באניוס | ~1,800m | ~1,800m altitude |

**⚠️ Risk:**
| Name | nameHe | reason (he) | reason (en) |
|------|--------|-------------|-------------|
| Amazon lodges (Tena, Coca) | לודג'ים באמזונס (טנה, קוקה) | אגן האמזונס | Amazon basin |
| Esmeraldas (north coast) | אסמרלדס (חוף צפוני) | חוף טרופי נמוך | Low tropical coast |

---

### 🇧🇴 Bolivia
Malaria: below 2500m, no risk in La Paz

**✅ Safe:**
| Name | nameHe | reason (he) | reason (en) |
|------|--------|-------------|-------------|
| La Paz | לה פאס | ~3,600m | ~3,600m altitude |
| Uyuni / Salar de Uyuni | אויוני / מדבר המלח | ~3,650m | ~3,650m altitude |
| Sucre | סוקרה | ~2,800m | ~2,800m altitude |
| Potosí | פוטוסי | ~4,000m | ~4,000m altitude |
| Lake Titicaca (Copacabana) | אגם טיטיקקה (קופקבנה) | ~3,800m | ~3,800m altitude |

**⚠️ Risk:**
| Name | nameHe | reason (he) | reason (en) |
|------|--------|-------------|-------------|
| Rurrenabaque / Pampas | רורנבאקה / פמפס | אמזונס | Amazon |
| Cochabamba (low areas) | קוצ'במבה (אזורים נמוכים) | חלקית | Partial |
| Santa Cruz de la Sierra | סנטה קרוז דה לה סיירה | ~400m | ~400m altitude |

---

### 🇬🇹 Guatemala
Malaria: Alta Verapaz, Baja Verapaz, Escuintla, Izabal, Petén

**✅ Safe:**
| Name | nameHe | reason (he) | reason (en) |
|------|--------|-------------|-------------|
| Antigua Guatemala | אנטיגואה גואטמלה | הרים, מרכז | Mountains, central |
| Guatemala City | גואטמלה סיטי | עירוני, מרכז | Urban, central |
| Lake Atitlán | אגם אטיטלן | הרים | Mountains |
| Chichicastenango | צ'יצ'יקסטננגו | הרים | Mountains |

**⚠️ Risk:**
| Name | nameHe | reason (he) | reason (en) |
|------|--------|-------------|-------------|
| Tikal | טיקאל | פטן | Petén |
| Flores | פלורס | פטן | Petén |
| Río Dulce / Livingston | ריו דולסה / ליווינגסטון | Izabal | Izabal |
| Semuc Champey | סמוק צ'מפיי | Alta Verapaz | Alta Verapaz |

---

### 🇨🇷 Costa Rica
Malaria: provinces Alajuela and Limón

**✅ Safe:**
| Name | nameHe | reason (he) | reason (en) |
|------|--------|-------------|-------------|
| San José | סן חוזה | מרכז, עירוני | Central, urban |
| Monteverde | מונטוורדה | הרים | Mountains |
| Manuel Antonio | מנואל אנטוניו | חוף מרכזי | Central coast |
| Guanacaste / Tamarindo | גואנקסטה / טמרינדו | צפון-מערב | Northwest |
| Santa Teresa | סנטה טרזה | חוף מערבי | West coast |

**⚠️ Risk:**
| Name | nameHe | reason (he) | reason (en) |
|------|--------|-------------|-------------|
| Arenal / La Fortuna | ארנל / לה פורטונה | Alajuela | Alajuela |
| Tortuguero | טורטוגרו | Limón | Limón |
| Puerto Viejo / Cahuita | פוארטו ויאחו / קאואיטה | Limón, חוף קריבי | Limón, Caribbean coast |

---

### 🇿🇦 South Africa
Malaria: along Zimbabwe/Mozambique border (Mopani, Vhembe in Limpopo + Mpumalanga)

**✅ Safe:**
| Name | nameHe | reason (he) | reason (en) |
|------|--------|-------------|-------------|
| Cape Town | קייפטאון | דרום-מערב | Southwest |
| Johannesburg | יוהנסבורג | מרכז, עירוני | Central, urban |
| Durban | דרבן | חוף מזרחי, דרומי | East coast, south |
| Garden Route | גארדן רוט | דרום | South |
| Stellenbosch / Winelands | סטלנבוש / אזור יינות | דרום-מערב | Southwest |

**⚠️ Risk:**
| Name | nameHe | reason (he) | reason (en) |
|------|--------|-------------|-------------|
| Kruger National Park | פארק קרוגר | מפומלנגה/לימפופו | Mpumalanga/Limpopo |
| Limpopo (northeast) | לימפופו (צפון-מזרח) | גבול | Border area |

---

### 🇰🇪 Kenya
Malaria: all areas below 2500m

**✅ Safe:**
| Name | nameHe | reason (he) | reason (en) |
|------|--------|-------------|-------------|
| Nairobi | ניירובי | ~1,700m, עירוני מרכזי | ~1,700m, central urban |

**⚠️ Risk:**
| Name | nameHe | reason (he) | reason (en) |
|------|--------|-------------|-------------|
| Masai Mara | מסאי מארה | סוואנה, נמוך | Savanna, low |
| Mombasa | מומבסה | חוף | Coast |
| Diani Beach | חוף דיאני | חוף | Coast |
| Amboseli | אמבוסלי | נמוך | Low altitude |
| Lake Nakuru | אגם נקורו | ~1,750m אבל מתחת ל-2500 | ~1,750m but below 2500 |
| Lamu | למו | חוף | Coast |

**Note**: Practically all tourist destinations except Nairobi are in risk zones.

---

### 🇪🇹 Ethiopia
Malaria: all areas below 2500m (including Addis Ababa)

**✅ Safe:**
| Name | nameHe | reason (he) | reason (en) |
|------|--------|-------------|-------------|
| Simien Mountains (trek) | הרי סימיאן (טרק) | מעל 3,000m | Above 3,000m |

**⚠️ Risk:**
| Name | nameHe | reason (he) | reason (en) |
|------|--------|-------------|-------------|
| Addis Ababa | אדיס אבבה | ~2,350m — מתחת לסף | ~2,350m — below threshold |
| Lalibela | לליבלה | ~2,500m — גבולי | ~2,500m — borderline |
| Gondar | גונדר | ~2,100m | ~2,100m |
| Bahir Dar / Lake Tana | באהיר דר / אגם טנה | ~1,800m | ~1,800m |
| Omo Valley | עמק אומו | נמוך | Low altitude |

**Note**: Opposite of Peru — almost everything is at risk, only the highest mountains are safe.

---

## Next Steps
1. Convert this data into `DATA_DESTINATIONS` JavaScript object
2. Add CSS for destination accordion inside country cards
3. Modify `renderCountryCard` to include accordion when destinations exist
4. Add i18n labels for the feature (he + en)
