import streamlit as st

# 💄 Aesthetic Title
st.markdown(
    "<h1 style='text-align:center; color:#ff4b8b;'>💄 Your Personal Makeup Recommender 💄</h1>",
    unsafe_allow_html=True
)

# Main Image
st.image("lipstick.jpg", use_container_width=True)

st.caption("Hey Cutie! 💕")
st.caption("💅 This is your Personalized makeup kit based on your budget and skin type")

# Sidebar
with st.sidebar:
    st.header("✨ Build your Kit!")
    Skin = st.selectbox("Skin Type", ["Dry", "Oily", "Combination"])
    Budget = st.slider("Select your budget (₹)", 1000, 5000, step=1000)
    Occasion = st.radio("Occasion", ["Daily", "Party", "Wedding"])
    build = st.button("✨ Build My Kit")

# When Button Clicked
if build:
    st.markdown("---")
    st.markdown("### 💖 Your Personalized Glam Kit ✨")

    # Decide foundation
    if Skin == "Dry":
        foundation = "Hydrating Foundation"
    elif Skin == "Oily":
        foundation = "Matte Foundation"
    else:
        foundation = "Natural Finish Foundation"

    # Create kit list
    kit = []
    kit.append(foundation)

    # Add products based on Budget
    if Budget <= 2000:
        kit.append("Compact Powder")
        kit.append("Lipstick")

    elif Budget <= 4000:
        kit.append("Compact Powder")
        kit.append("Concealer")
        kit.append("Eyeliner")
        kit.append("Lipstick")

    else:
        kit.append("Compact Powder")
        kit.append("Concealer")
        kit.append("Mascara")
        kit.append("Eyeshadow Palette")
        kit.append("Premium Lipstick")

    # Modify based on Occasion
    if Occasion == "Wedding":
        kit.append("Highlighter ✨")
    elif Occasion == "Party":
        kit.append("Bold Lipstick 💄")

    # Display kit items
    for item in kit:
        st.markdown(f"💗 {item}")

    st.markdown("---")
    st.success("✨ Your glam kit is ready! Slay the day queen 💅💖")

    # 🎀 Inspiration Section (Side-by-Side)
    st.markdown("### ✨ Your Look Inspiration")

    col1, col2 = st.columns(2)

    with col1:
        if Occasion == "Daily":
            st.image("daily.jpg", use_container_width=True)
        elif Occasion == "Party":
            st.image("hands.jpg", use_container_width=True)
        elif Occasion == "Wedding":
            st.image("milky.jpg", use_container_width=True)

    with col2:
        if Occasion == "Daily":
            st.markdown("🌸 **Soft Everyday Glow**  \nKeep it fresh, light and natural.")
        elif Occasion == "Party":
            st.markdown("💃 **Bold Glam Look**  \nTime to sparkle and stand out!")
        elif Occasion == "Wedding":
            st.markdown("👰 **Bridal Radiance**  \nGlow like the main character ✨")