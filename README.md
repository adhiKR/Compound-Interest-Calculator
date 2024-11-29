import streamlit as st

st.title("Future Value Calculator")
principal = st.number_input("Principal Amount", value=100000)
rate = st.slider("Rate of Interest (p.a.)", 0.1, 20.0, 6.0, step=0.1)
time = st.slider("Time Period (Years)", 1, 30, 5)
frequency = st.selectbox("Compounding Frequency", ["Yearly", "Half-Yearly", "Quarterly", "Monthly", "Daily"])

freq_mapping = {
    "Yearly": 1,
    "Half-Yearly": 2,
    "Quarterly": 4,
    "Monthly": 12,
    "Daily": 365
}

n = freq_mapping[frequency]
future_value = principal * (1 + (rate / 100) / n) ** (n * time)

st.write(f"Future Value: ₹{future_value:,.2f}")
