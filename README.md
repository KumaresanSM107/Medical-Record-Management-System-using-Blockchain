import hashlib
import time
import json

class Block:
    def __init__(self, index, timestamp, data, previous_hash, nonce=0):
        self.index = index
        self.timestamp = timestamp
        self.data = data
        self.previous_hash = previous_hash
        self.nonce = nonce
        self.hash = self.compute_hash()

    def compute_hash(self):
        block_string = json.dumps({
            'index': self.index,
            'timestamp': self.timestamp,
            'data': self.data,
            'previous_hash': self.previous_hash,
            'nonce': self.nonce
        }, sort_keys=True)
        return hashlib.sha256(block_string.encode()).hexdigest()

    def mine(self, difficulty):
        prefix = '0' * difficulty
        while not self.hash.startswith(prefix):
            self.nonce += 1
            self.hash = self.compute_hash()

class Blockchain:
    def __init__(self):
        self.chain = []
        self.difficulty = 2
        self.create_genesis_block()

    def create_genesis_block(self):
        genesis_block = Block(0, time.time(), {"message": "Genesis Block"}, "0")
        genesis_block.mine(self.difficulty)
        self.chain.append(genesis_block)

    def get_latest_block(self):
        return self.chain[-1]

    def add_block(self, data):
        index = len(self.chain)
        previous_hash = self.get_latest_block().hash
        new_block = Block(index, time.time(), data, previous_hash)
        new_block.mine(self.difficulty)
        self.chain.append(new_block)

    def is_chain_valid(self):
        for i in range(1, len(self.chain)):
            curr = self.chain[i]
            prev = self.chain[i - 1]

            if curr.hash != curr.compute_hash():
                return False

            if curr.previous_hash != prev.hash:
                return False

        return True

    def print_chain(self):
        for block in self.chain:
            print("\n====================")
            print(f"Index: {block.index}")
            print(f"Timestamp: {time.ctime(block.timestamp)}")
            print(f"Data: {block.data}")
            print(f"Hash: {block.hash}")
            print(f"Previous Hash: {block.previous_hash}")
            print(f"Nonce: {block.nonce}")

# -------------------------------
# Simulated Medical Record System
# -------------------------------

def main():
    medical_chain = Blockchain()

    while True:
        print("\n--- Medical Record Blockchain System ---")
        print("1. Add Medical Record")
        print("2. View Blockchain")
        print("3. Check Integrity")
        print("4. Exit")
        choice = input("Enter choice: ")

        if choice == '1':
            patient_id = input("Enter Patient ID: ")
            diagnosis = input("Enter Diagnosis: ")
            treatment = input("Enter Treatment: ")

            record = {
                "patient_id": patient_id,
                "diagnosis": diagnosis,
                "treatment": treatment,
                "timestamp": time.ctime()
            }

            print("Mining block...")
            medical_chain.add_block(record)
            print("✔ Record added successfully!")

        elif choice == '2':
            print("\n--- Blockchain Ledger ---")
            medical_chain.print_chain()

        elif choice == '3':
            if medical_chain.is_chain_valid():
                print("✅ Blockchain is valid.")
            else:
                print("❌ Blockchain has been compromised!")

        elif choice == '4':
            break
        else:
            print("Invalid option!")

if __name__ == "__main__":
    main()
import hashlib
import time
import json

class Block:
    def __init__(self, index, timestamp, data, previous_hash, nonce=0):
        self.index = index
        self.timestamp = timestamp
        self.data = data
        self.previous_hash = previous_hash
        self.nonce = nonce
        self.hash = self.compute_hash()

    def compute_hash(self):
        block_string = json.dumps({
            'index': self.index,
            'timestamp': self.timestamp,
            'data': self.data,
            'previous_hash': self.previous_hash,
            'nonce': self.nonce
        }, sort_keys=True)
        return hashlib.sha256(block_string.encode()).hexdigest()

    def mine(self, difficulty):
        prefix = '0' * difficulty
        while not self.hash.startswith(prefix):
            self.nonce += 1
            self.hash = self.compute_hash()

class Blockchain:
    def __init__(self):
        self.chain = []
        self.difficulty = 2
        self.create_genesis_block()

    def create_genesis_block(self):
        genesis_block = Block(0, time.time(), {"message": "Genesis Block"}, "0")
        genesis_block.mine(self.difficulty)
        self.chain.append(genesis_block)

    def get_latest_block(self):
        return self.chain[-1]

    def add_block(self, data):
        index = len(self.chain)
        previous_hash = self.get_latest_block().hash
        new_block = Block(index, time.time(), data, previous_hash)
        new_block.mine(self.difficulty)
        self.chain.append(new_block)

    def is_chain_valid(self):
        for i in range(1, len(self.chain)):
            curr = self.chain[i]
            prev = self.chain[i - 1]

            if curr.hash != curr.compute_hash():
                return False

            if curr.previous_hash != prev.hash:
                return False

        return True

    def print_chain(self):
        for block in self.chain:
            print("\n====================")
            print(f"Index: {block.index}")
            print(f"Timestamp: {time.ctime(block.timestamp)}")
            print(f"Data: {block.data}")
            print(f"Hash: {block.hash}")
            print(f"Previous Hash: {block.previous_hash}")
            print(f"Nonce: {block.nonce}")

# -------------------------------
# Simulated Medical Record System
# -------------------------------

def main():
    medical_chain = Blockchain()

    while True:
        print("\n--- Medical Record Blockchain System ---")
        print("1. Add Medical Record")
        print("2. View Blockchain")
        print("3. Check Integrity")
        print("4. Exit")
        choice = input("Enter choice: ")

        if choice == '1':
            patient_id = input("Enter Patient ID: ")
            diagnosis = input("Enter Diagnosis: ")
            treatment = input("Enter Treatment: ")

            record = {
                "patient_id": patient_id,
                "diagnosis": diagnosis,
                "treatment": treatment,
                "timestamp": time.ctime()
            }

            print("Mining block...")
            medical_chain.add_block(record)
            print("✔ Record added successfully!")

        elif choice == '2':
            print("\n--- Blockchain Ledger ---")
            medical_chain.print_chain()

        elif choice == '3':
            if medical_chain.is_chain_valid():
                print("✅ Blockchain is valid.")
            else:
                print("❌ Blockchain has been compromised!")

        elif choice == '4':
            break
        else:
            print("Invalid option!")

if __name__ == "__main__":
    main()
