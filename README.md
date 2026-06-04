import streamlit as st
import datetime

# Setup a clean mobile layout view
st.set_page_config(page_title="Alignment Journal", page_icon="📝", layout="centered")

st.title("📱 Daily Alignment Journal")
st.markdown("*Real growth is becoming more honest, more aware, less defensive, and a little easier to love.*")
st.markdown("---")

# Today's Date Picker
entry_date = st.date_input("Select Entry Date", datetime.date.today())

st.markdown("### 1. Baggage Check & Awareness")
ego_ans = st.text_area("Ego & Defensiveness", placeholder="Did I react out of pride or a need to be right today? Where could I have chosen humility?", key="ego")
assumptions_ans = st.text_area("Assumptions Check", placeholder="Did I mind-read or assign negative intentions to others today?", key="assumptions")

st.markdown("### 2. Emotional Regulation & Accountability")
rope_ans = st.text_area("My Side of the Rope", placeholder="If friction arose today, what was my part in it? Did I own it?", key="rope")
climate_ans = st.text_area("Internal Climate", placeholder="Did I self-regulate, or did I map my discomfort or bad day onto others?", key="climate")

st.markdown("### 3. Curiosity Over Reaction")
trigger_ans = st.text_area("Trigger Roots", placeholder="Did a comment sting? Is this a current issue, or an older wound resurfacing?", key="triggers")

st.markdown("### 4. Radical Expression")
expression_ans = st.text_area("Opening the Box", placeholder="Did I clearly state my needs and expectations, or did I stay silent and expect mind-reading?", key="expression")

st.markdown("### 🏆 Daily Alignment Scorecard")
st.caption("Rate your alignment from 1 (Room to grow) to 5 (Deep awareness)")
col1, col2 = st.columns(2)
with col1:
    h_score = st.slider("Honesty & Awareness", 1, 5, 3)
    d_score = st.slider("Shedding Defensiveness", 1, 5, 3)
with col2:
    a_score = st.slider("Accountability", 1, 5, 3)
    c_score = st.slider("Clear Connection", 1, 5, 3)

st.markdown("### 📝 Evening Reflection")
reflection_ans = st.text_area("One victory today, and one pattern to consciously intercept tomorrow:", key="reflection")

st.markdown("---")
if st.button("💾 Save Daily Log Entry", type="primary"):
    st.success(f"🎉 Journal Entry for {entry_date} Formatted Successfully!")
    
    log_summary = f"""
📅 ENTRY DATE: {entry_date}
----------------------------------------
1. BAGGAGE CHECK & AWARENESS
• Ego & Defensiveness: {ego_ans}
• Assumptions: {assumptions_ans}

2. EMOTIONAL REGULATION
• My Side of the Rope: {rope_ans}
• Internal Climate: {climate_ans}

3. CURIOSITY OVER REACTION
• Trigger Roots: {trigger_ans}

4. RADICAL EXPRESSION
• Expectations & Needs: {expression_ans}

🏆 SCORES
• Honesty: {h_score}/5 | Defensiveness: {d_score}/5
• Accountability: {a_score}/5 | Connection: {c_score}/5

📝 REFLECTION
• Victory & Interception: {reflection_ans}
    """
    st.text_area("Copy/Paste Data Log Summary:", value=log_summary, height=300)
    