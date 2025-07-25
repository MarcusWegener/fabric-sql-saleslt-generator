# fabric-sql-saleslt-generator

**Scalable data generator for AdventureWorksLT in Microsoft Fabric SQL.**  
Create up to 100,000+ synthetic sales orders for realistic demo and training scenarios.

---

## 🧩 About this project

When recording some [Power BI training videos on YouTube](https://youtu.be/gZ2p0_yaAtY?si=Jp3UJri1gcCr2PUt) a while ago, I used the **AdventureWorksLT** database as a data source. This database can easily be deployed on **Azure SQL** via the Azure portal and was perfect—until I realized (mid-recording!) that the available sales data was extremely limited: most orders are confined to a single day.

More recently, during another training session, a participant asked if I could provide the same sample database used in the videos. I didn’t want to burden non-technical users with setting up an Azure SQL Database (and an Azure subscription), but thankfully things have changed.

With just a few clicks, you can now deploy a **Microsoft Fabric SQL Database** and load the AdventureWorksLT dataset into it—without needing Azure subscriptions or infrastructure setup.  
📚 See:
- [Create a Fabric SQL database](https://learn.microsoft.com/fabric/database/sql/tutorial-create-database?WT.mc_id=DP-MVP-5004288)
- [Ingest data into Fabric SQL](https://learn.microsoft.com/fabric/database/sql/tutorial-ingest-data?WT.mc_id=DP-MVP-5004288)

However, the dataset still includes only a few sales records. To solve that, I created this SQL script, which allows you to **generate a large number of synthetic sales orders** with corresponding order details. It’s not a perfect solution yet—but it’s a solid starting point to quickly generate meaningful data for your demos, reports, and trainings.

---

## 🚀 What the script does

- Inserts synthetic rows into `SalesOrderHeader` and `SalesOrderDetail` using real `Customer`, `Product`, and `Address` data.
- Randomizes:
  - Order quantities
  - Product combinations
  - Order dates (within the past 3 years)
- Computes `SubTotal`, `TaxAmt`, and `Freight` values.
- Includes a `Comment` tag (`'Generated by Script'`) so that records can be easily removed later.
- Can generate **100,000+ rows** in a single execution.

---

## 🛠 How to use

1. Deploy **AdventureWorksLT** in a **Microsoft Fabric SQL database** (see links above).
2. Copy and run the [`sql/generate-sales-orders.sql`](./sql/generate-sales-orders.sql) script inside the Fabric SQL query editor.
3. Review and explore your new sales data in Power BI or via direct queries.

---

## 🧹 Optional: Clean up

The script includes optional `DELETE` statements to remove all generated data, making it easy to reset your database.

---

## 🤝 Contributions welcome

Feel free to fork, adapt, or improve the script! If you have ideas on making it more realistic or want to add additional dimensions (like territories, returns, or seasonal variation), I’d love to see your contributions.

---

## 📧 Contact

Questions or feedback?  
Reach out via [LinkedIn](https://www.linkedin.com/in/marcuswegener/) or open an issue here.

---

## 📄 License

[MIT License](./LICENSE)
