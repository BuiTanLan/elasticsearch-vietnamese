# elasticsearch-vietnamese

**Disclaimer**
Fixed me if you have any idea to make Docker steps cleaner

- This repo is for single node ES, you can update the docker build as your requirements.
- You must run these steps on Linux, OSX, Windows(WSL2) and install necessary commands like cmake, javac, mvn.

# Steps to add Vietnamese es plugin

## TL;DR:

1. Clone the cococ library repository

```sh
git clone https://github.com/coccoc/coccoc-tokenizer.git
cd coccoc-tokenizer && mkdir build && cd build
cmake -DBUILD_JAVA=1 ..
make install
```

2. Copy the `/usr/local/share/tokenizer/dicts` folder to this repo `/elasticsearch/dicts` directory

3. Clone the plugin

```sh
git clone https://github.com/duydo/elasticsearch-analysis-vietnamese.git
```

Update `elasticsearch-analysis-vietnamese/pom.xml` file to expected version (I'm using latest version `7.17.1`)

```xml
<groupId>org.elasticsearch</groupId>
<artifactId>elasticsearch-analysis-vietnamese</artifactId>
<version>7.17.1</version>
```

then run `mvn package` to build the plugin

4. Clone this repository

5. Copy the `elasticsearch-analysis-vietnamese/target/release/elasticsearch-analysis-vietnamese-7.17.1.zip` or `elasticsearch-analysis-vietnamese/release/elasticsearch-analysis-vietnamese-7.17.1.zip` folder to this repo `elasticsearch-vietnamese/elasticsearch/` directory

6. Update the version in `.env` file to match with the version of plugin

7. Run command: `docker compose up -d`
