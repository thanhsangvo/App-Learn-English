# Implementation Plan - Shopee Profit Calculator

## Goal Description
Create a modern, mobile-friendly Streamlit web application to calculate Shopee sales profit. The app will take various costs and fees into account, calculate the final profit and margin, and visualize the cost distribution.

## User Review Required
> [!NOTE]
> Assuming "Thuế 1.5% trên doanh thu" is calculated directly on the Selling Price.
> assuming "Phí sàn", "Phí thanh toán", "Phí Freeship Xtra" are percentages of the Selling Price.

## Proposed Changes

### Project Structure
#### [NEW] [app.py](file:///Users/devsang/Downloads/untitled%20folder/app.py)
- Main Streamlit application.
- **Inputs**:
    - Selling Price (Giá bán)
    - Cost Price (Giá vốn)
    - Payment Fee % (Phí thanh toán)
    - Platform Fee % (Phí sàn)
    - Freeship Xtra Fee % (Phí Freeship Xtra)
    - Fixed Fee (Phí cố định)
- **Logic**:
    - Tax = Selling Price * 1.5%
    - Fee Amounts = Selling Price * (Fee % / 100)
    - Total Cost = Cost Price + Fees + Tax
    - Profit = Selling Price - Total Cost
    - Margin = (Profit / Selling Price) * 100
- **Visualization**:
    - Interactive Pie Chart using `plotly.express` showing:
        - Giá vốn
        - Các loại phí sàn (Payment + Platform + Freeship + Fixed)
        - Thuế
        - Lợi nhuận
- **UI**:
    - Use `st.columns` for responsive layout.
    - Custom CSS for better mobile appearance if necessary.

#### [NEW] [requirements.txt](file:///Users/devsang/Downloads/untitled%20folder/requirements.txt)
- streamlit
- pandas
- plotly

## Verification Plan

### Automated Tests
- None planned for this simple script.

### Manual Verification
1. Run the app: `streamlit run app.py`
2. Input test values:
    - Selling Price: 100,000
    - Cost: 50,000
    - Fees: 2%, 3%, 4%...
3. Verify calculations match manual calculation.
4. Verify Pie Chart renders correctly.
5. Resize window to check responsiveness.
