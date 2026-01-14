# Notebooks Repository

This repository contains Jupyter notebooks for various AI and machine learning projects.

## Setup

### Prerequisites
- Python 3.8+
- OpenAI API key

### Installation

1. Clone the repository:
```bash
git clone <your-repo-url>
cd notebooks
```

2. Install required packages:
```bash
pip install faiss-cpu openai numpy jupyter
```

3. Set up your OpenAI API key:

**Option 1: Environment Variable (Recommended)**
```bash
export OPENAI_API_KEY='your-api-key-here'
```

**Option 2: For persistent use, add to your shell profile:**
```bash
echo 'export OPENAI_API_KEY="your-api-key-here"' >> ~/.bashrc
source ~/.bashrc
```

**Option 3: Using .env file (for local development)**
```bash
echo 'OPENAI_API_KEY=your-api-key-here' > .env
```

### For GitHub Actions/Codespaces

To use this notebook in GitHub Actions or Codespaces:

1. Go to your GitHub repository Settings
2. Navigate to **Secrets and variables** → **Actions**
3. Click **New repository secret**
4. Name: `OPENAI_API_KEY`
5. Value: Your OpenAI API key
6. Click **Add secret**

The notebook will automatically read the key from the environment.

## Notebooks

### faiss_vector_db.ipynb
A complete implementation of a vector database using Faiss and OpenAI embeddings.

**Features:**
- Load documents from text files
- Generate embeddings using OpenAI API
- Store embeddings in Faiss vector database
- Perform similarity search
- Test with multiple queries

**Usage:**
```bash
jupyter notebook faiss_vector_db.ipynb
```

## Security Best Practices

⚠️ **NEVER commit API keys to the repository!**

- Always use environment variables for sensitive data
- The `.gitignore` file is configured to exclude common secret files
- Use GitHub Secrets for CI/CD workflows
- Review commits before pushing to ensure no secrets are included

## Contributing

Feel free to add more notebooks and improve existing ones!

## License

MIT License
