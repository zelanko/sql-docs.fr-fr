---
title: Mode FIPS dans JDBC | Microsoft Docs
ms.custom: ''
ms.date: 03/26/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: genemi
ms.technology: connectivity
ms.topic: conceptual
author: MikeRayMSFT
ms.author: mikeray
manager: kenvh
ms.openlocfilehash: 482e820d17860b67f46d47f4bb8523e833d0cf5a
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68252213"
---
# <a name="fips-mode"></a>Mode FIPS

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Le pilote Microsoft JDBC pour SQL Server prend en charge l’exécution dans JVM configuré pour être conforme à la norme *FIPS 140*.

#### <a name="prerequisites"></a>Conditions préalables requises

- JVM configuré par FIPS
- Certificat SSL approprié
- Fichiers de stratégie appropriés
- Paramètres de configuration appropriés

## <a name="fips-configured-jvm"></a>JVM configuré par FIPS

En règle générale, les applications `java.security` peuvent configurer le fichier pour utiliser des fournisseurs de chiffrement compatibles FIPS. Pour savoir comment configurer la conformité FIPS 140, consultez la documentation spécifique à votre machine virtuelle Java.

Pour afficher la configuration des modules approuvés pour FIPS, reportez-vous à [modules validés dans le programme de validation du module](https://csrc.nist.gov/Projects/cryptographic-module-validation-program/Validated-Modules)de chiffrement.

Les fournisseurs peuvent avoir des étapes supplémentaires pour configurer une machine virtuelle Java avec FIPS.

## <a name="appropriate-ssl-certificate"></a>Certificat SSL approprié
Pour vous connecter à SQL Server en mode FIPS, vous devez disposer d’un certificat SSL valide. Installez-le ou importez-le dans le magasin de clés Java sur l’ordinateur client (JVM) sur lequel FIPS est activé.

### <a name="importing-ssl-certificate-in-java-keystore"></a>Importation du certificat SSL dans le magasin de clés Java
Pour FIPS, il est très probable que vous deviez importer le certificat (. cert) dans PKCS ou dans un format spécifique au fournisseur.
Utilisez l’extrait de code suivant pour importer le certificat SSL et le stocker dans un répertoire de travail avec le format de magasin de clés approprié. _Le\_mot\_de passe du magasin_ d’approbations est votre mot de passe pour le magasin de clés Java.

```java
public void saveGenericKeyStore(
        String provider,
        String trustStoreType,
        String certName,
        String certPath
        ) throws KeyStoreException, CertificateException,
            NoSuchAlgorithmException, NoSuchProviderException,
            IOException
{
    KeyStore ks = KeyStore.getInstance(trustStoreType, provider);
    FileOutputStream os = new FileOutputStream("./MyTrustStore_" + trustStoreType);
    ks.load(null, null);
    ks.setCertificateEntry(certName, getCertificate(certPath));
    ks.store(os, TRUST_STORE_PASSWORD.toCharArray());
    os.flush();
    os.close();
}

private Certificate getCertificate(String pathName)
        throws FileNotFoundException, CertificateException
{
    FileInputStream fis = new FileInputStream(pathName);
    CertificateFactory cf = CertificateFactory.getInstance("X.509");
    return cf.generateCertificate(fis);
}
```

L’exemple suivant consiste à importer un certificat Azure SSL au format PKCS12 avec le fournisseur BouncyCastle. Le certificat est importé dans le répertoire de travail _nommé\_MyTrustStore PKCS12_ à l’aide de l’extrait de code suivant:

`saveGenericKeyStore(BCFIPS, PKCS12, "SQLAzure SSL Certificate Name", "SQLAzure.cer");`

## <a name="appropriate-policy-files"></a>Fichiers de stratégie appropriés
Pour certains fournisseurs FIPS, des fichiers jar de stratégie illimités sont nécessaires. Dans ce cas, pour Sun/Oracle, téléchargez les fichiers de stratégie de la juridiction de la force de performance illimitée de Java Cryptography Extension (JCE) pour [JRE 8](https://www.oracle.com/technetwork/java/javase/downloads/jce8-download-2133166.html) ou [JRE 7](https://www.oracle.com/technetwork/java/javase/downloads/jce-7-download-432124.html). 

## <a name="appropriate-configuration-parameters"></a>Paramètres de configuration appropriés
Pour exécuter le pilote JDBC en mode compatible FIPS, configurez les propriétés de connexion comme indiqué dans le tableau suivant. 

#### <a name="properties"></a>Propriétés 

|Propriété|Type|Valeur par défaut|Description|Remarques|
|---|---|---|---|---|
|encrypt|Booléen [« true / false »]|"false"|Pour la propriété de chiffrement JVM activée pour FIPS, la propriété doit avoir la **valeur true**||
|TrustServerCertificate|Booléen [« true / false »]|"false"|Pour FIPS, l’utilisateur doit valider la chaîne de certificats, de sorte que l’utilisateur doit utiliser la valeur **«false»** pour cette propriété. ||
|trustStore|String|Null|Le chemin d’accès à votre fichier keystore Java où vous avez importé votre certificat. Si vous installez le certificat sur votre système, vous n’avez rien à faire. Le pilote utilise des cacerts ou des fichiers jssecacerts.||
|trustStorePassword|String|Null|Mot de passe utilisé pour vérifier l'intégrité des données trustStore.||
|fips|Booléen [« true / false »]|"false"|Pour la machine virtuelle Java activée pour FIPS, cette propriété doit avoir la **valeur true**|Ajouté au point 6.1.4 (version 6.2.2 stable)||
|fipsProvider|String|Null|Fournisseur FIPS configuré dans JVM. Par exemple, BCFIPS ou SunPKCS11-NSS |Ajouté au point 6.1.2 (version 6.2.2 stable), déconseillé dans 6.4.0-consultez les détails [ici](https://github.com/Microsoft/mssql-jdbc/pull/460).|
|trustStoreType|String|JKS|Pour le mode FIPS, définissez le type de magasin d’approbation PKCS12 ou le type défini par le fournisseur FIPS. |Ajouté à 6.1.2 (version en 6.2.2 stable)||
| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |
