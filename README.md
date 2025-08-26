🏥 Medical Record Management System Using Blockchain

A robust and secure medical record management system built using a custom Python-based blockchain. It ensures that each patient’s data is immutable, cryptographically secured, and transparently recorded through a verifiable chain of trust. This project demonstrates how blockchain technology can be effectively applied in the healthcare domain for data integrity, security, and traceability.

🚀 Features

🔐 Tamper-proof medical records using SHA-256 hashing

⛓️ Linked block structure ensuring complete traceability

⛏️ Proof-of-Work for block validation

📅 Timestamped patient history records

🧪 Chain integrity verification

🐍 100% Python, no external dependencies

📂 Project Structure

medical-record-blockchain/
├── blockchain_medical.py # Main Python script
├── README.md # Project documentation
├── LICENSE # MIT License
└── .gitignore # Ignore cache and environment files

▶️ Getting Started
Requirements

Python 3.6 or higher

Run the Application
python blockchain_medical.py


You’ll see a CLI menu to:

Add new medical records

View the blockchain ledger

Verify blockchain integrity

🧠 How It Works

Each block in the blockchain includes:

Patient ID

Diagnosis

Treatment

Timestamp

Hash of the current block

Hash of the previous block

Blocks are mined using a simplified Proof-of-Work algorithm, ensuring each record’s integrity and resistance to tampering.

💡 Future Enhancements

Add encryption for patient data privacy

Web interface using Flask or Django

Integration with real hospital databases

Role-based access (doctor, admin, patient)

Smart contract-based treatment automation

📄 License

This project is licensed under the MIT License — see the LICENSE file for details.

🧾 Project Summary

A high-integrity medical record system built on a custom Python blockchain. Each record is cryptographically secured, immutable, and linked using Proof-of-Work. Demonstrates how blockchain ensures trust, transparency, and data security in healthcare systems
