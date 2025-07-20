#  MinIo

MinIO és un sistema d’emmagatzematge d’objectes altament escalable, compatible amb l’API S3 d’Amazon, i dissenyat per ser:

    - Lleuger
    - Molt ràpid
    - Segur
    - Fàcil de desplegar, tant en local com en producció (kubernetes, cloud, etc.)

---
```docker run -p 9000:9000 -p 9001:9001 \
  -e "MINIO_ROOT_USER=admin" \
  -e "MINIO_ROOT_PASSWORD=admin123" \
  -v /home/xavi/minio:/data \
  quay.io/minio/minio server /data --console-address ":9001"
```
 
 ---
## Què és mc (MinIO Client)?

mc és una eina de línia de comandes que funciona de manera similar a aws cli, però pensada per a:

    - MinIO
    - Amazon S3
    - Altres serveis S3-compatibles (Ceph, DigitalOcean Spaces, etc.)

## Instal·lació de mc

En Linux / macOS:
```
curl -O https://dl.min.io/client/mc/release/linux-amd64/mc
chmod +x mc
sudo mv mc /usr/local/bin/
```

## Com es fa servir?

### 1. Configura l'accés al teu servidor MinIO:

``` mc alias set local http://localhost:9000 admin admin123 ```

local és un nom que li poses al servidor

http://localhost:9000 és l’endpoint

admin i admin123 són l’usuari i la contrasenya

### 2. Crear un bucket:

``` mc mb local/meu-bucket ```

### 3. Pujar un fitxer:

``` mc cp text.txt local/meu-bucket ```

### 4. Veure els buckets i fitxers:

```
mc ls local
mc ls local/meu-bucket
```
