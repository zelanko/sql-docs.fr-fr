---
title: Mode FIPS dans JDBC | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: genemi
ms.technology: connectivity
ms.topic: conceptual
author: MikeRayMSFT
ms.author: mikeray
manager: kenvh
ms.openlocfilehash: 63681ee474d4993e248bf02dcabd9065317ffa39
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "69028066"
---
# <a name="fips-mode"></a>Mode FIPS

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Le pilote Microsoft JDBC pour SQL Server prend en charge l’exécution dans des JVM configurées pour être *compatibles FIPS 140*.

#### <a name="prerequisites"></a>Conditions préalables requises

- Machine virtuelle Java configurée selon FIPS
- Certificat SSL approprié
- Fichiers de stratégie appropriés
- Paramètres de configuration appropriés

## <a name="fips-configured-jvm"></a>Machine virtuelle Java configurée selon FIPS

En règle générale, les applications peuvent configurer le fichier `java.security` pour utiliser des fournisseurs de chiffrement compatibles FIPS. Pour savoir comment configurer la conformité FIPS 140, consultez la documentation spécifique à votre machine virtuelle Java.

Pour voir les modules approuvés pour la configuration FIPS, reportez-vous à [Modules validés dans le programme de validation des modules de chiffrement](https://csrc.nist.gov/Projects/cryptographic-module-validation-program/Validated-Modules).

Les fournisseurs peuvent avoir à effectuer des étapes supplémentaires pour configurer une machine virtuelle Java en mode FIPS.

## <a name="appropriate-ssl-certificate"></a>Certificat SSL approprié
Pour vous connecter à SQL Server en mode FIPS, vous devez disposer d’un certificat SSL valide. Installez-le ou importez-le dans le magasin de clés Java sur l’ordinateur client (JVM) où FIPS est activé.

### <a name="importing-ssl-certificate-in-java-keystore"></a>Importation du certificat SSL dans le magasins de clés Java
Pour FIPS, vous devrez très probablement importer le certificat (.cert) dans PKCS ou dans un format spécifique au fournisseur.
Utilisez l’extrait de code suivant pour importer le certificat SSL et le stocker dans un répertoire de travail au format de magasin de clés approprié. _TRUST\_STORE\_PASSWORD_ est votre mot de passe pour le magasin de clés Java.

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

L’exemple suivant montre l’importation d’un certificat Azure SSL au format PKCS12 avec le fournisseur BouncyCastle. Le certificat est importé dans le répertoire de travail nommé _MyTrustStore\_PKCS12_ à l’aide de l’extrait de code suivant :

`saveGenericKeyStore(BCFIPS, PKCS12, "SQLAzure SSL Certificate Name", "SQLAzure.cer");`

## <a name="appropriate-policy-files"></a>Fichiers de stratégie appropriés
Pour certains fournisseurs FIPS, des fichiers JAR de stratégie illimités sont nécessaires. Dans de tels cas, pour Sun/Oracle, téléchargez les fichiers de stratégie de compétence de force illimitée d’extension de chiffrement Java (JCE) pour [JRE 8](https://www.oracle.com/technetwork/java/javase/downloads/jce8-download-2133166.html) ou [JRE 7](https://www.oracle.com/technetwork/java/javase/downloads/jce-7-download-432124.html). 

## <a name="appropriate-configuration-parameters"></a>Paramètres de configuration appropriés
Pour exécuter le pilote JDBC en mode compatible FIPS, configurez les propriétés de connexion comme indiqué dans le tableau suivant. 

#### <a name="properties"></a>Propriétés 

|Propriété|Type|Default|Description|Notes|
|---|---|---|---|---|
|encrypt|Booléen [« true / false »]|"false"|Pour le chiffrement de la machine virtuelle Java activée pour FIPS, la propriété doit être **true**||
|TrustServerCertificate|Booléen [« true / false »]|"false"|Pour FIPS, l’utilisateur doit valider la chaîne de certificats, de sorte que l’utilisateur doit utiliser la valeur de **false** pour cette propriété. ||
|trustStore|String|null|Chemin du fichier de magasins de clés Java où vous avez importé votre certificat. Si vous installez le certificat sur votre système, vous n’avez rien à faire. Le pilote utilise des fichiers cacerts ou jssecacerts.||
|trustStorePassword|String|null|Mot de passe utilisé pour vérifier l'intégrité des données trustStore.||
|fips|Booléen [« true / false »]|"false"|Pour la machine virtuelle Java activée pour FIPS, la propriété doit être **true**|Ajouté au point 6.1.4 (version 6.2.2 stable)||
|fipsProvider|String|null|Fournisseur FIPS configuré dans la machine virtuelle Java. Par exemple, BCFIPS ou SunPKCS11-NSS |Ajouté au point 6.1.2 (version 6.2.2 stable), déconseillé dans 6.4.0 : consultez les détails [ici](https://github.com/Microsoft/mssql-jdbc/pull/460).|
|trustStoreType|String|JKS|Pour le mode FIPS, définissez le type de magasin de confiance PKCS12 ou le type défini par le fournisseur FIPS |Ajouté au point 6.1.2 (version 6.2.2 stable)||
| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |
