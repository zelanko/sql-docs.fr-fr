---
title: Mode FIPS sur JDBC | Microsoft Docs
ms.custom: ''
ms.date: 03/26/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: craigg
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daveng
manager: kenvh
ms.openlocfilehash: 8fb6ea7bf6abfb1f347d0541a01bae91aacf5f1c
ms.sourcegitcommit: 0c049c539ae86264617672936b31d89456d63bb0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58618276"
---
# <a name="fips-mode"></a>Mode FIPS
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Microsoft JDBC Driver for SQL Server prend en charge en cours d’exécution dans les machines virtuelles Java configuré pour être *FIPS 140 conformes*.

#### <a name="prerequisites"></a>Conditions préalables requises

- FIPS configuré JVM
- Certificat SSL approprié
- Fichiers de stratégie appropriée
- Paramètres de Configuration approprié

## <a name="fips-configured-jvm"></a>FIPS configuré JVM

En règle générale, les applications peuvent configurer le `java.security` fichier à utiliser des fournisseurs de services de chiffrement compatible FIPS. Consultez la documentation spécifique à votre machine virtuelle Java pour savoir comment configurer la conformité aux normes FIPS 140.

Pour afficher les modules approuvés pour la Configuration de la norme FIPS, reportez-vous à [validé des Modules dans le programme de Validation de Module de chiffrement](https://csrc.nist.gov/Projects/cryptographic-module-validation-program/Validated-Modules).

Les fournisseurs peuvent avoir des étapes supplémentaires pour configurer une machine virtuelle Java à la norme FIPS.

## <a name="appropriate-ssl-certificate"></a>Certificat SSL approprié
Pour vous connecter à SQL Server en mode FIPS, un certificat SSL valide est requis. Installer ou l’importer dans le Store de clé Java sur l’ordinateur client (JVM) où FIPS est activé.

### <a name="importing-ssl-certificate-in-java-keystore"></a>L’importation de certificat SSL dans le magasin de clés de Java
Pour FIPS, très probablement vous devez importer le certificat (.cert) dans un format spécifique au fournisseur ou PKCS.
Utilisez l’extrait de code suivant pour importer le certificat SSL et stockez-le dans un répertoire de travail avec le format de magasin de clés approprié. _APPROBATION\_STORE\_mot de passe_ concerne votre mot de passe KeyStore Java.

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

L’exemple suivant importe un certificat SSL de Azure au format PKCS12 avec le fournisseur BouncyCastle. Le certificat est importé dans le répertoire de travail nommé _MyTrustStore\_PKCS12_ à l’aide de l’extrait de code suivant :

`saveGenericKeyStore(BCFIPS, PKCS12, "SQLAzure SSL Certificate Name", "SQLAzure.cer");`

## <a name="appropriate-policy-files"></a>Fichiers de stratégie appropriée
Pour certains fournisseurs FIPS, les fichiers JAR de stratégie unrestricted sont nécessaires. Dans ce cas, Sun / Oracle, téléchargez les Java Cryptography Extension (JCE) illimité force juridiction stratégie fichiers [JRE 8](https://www.oracle.com/technetwork/java/javase/downloads/jce8-download-2133166.html) ou [JRE 7](https://www.oracle.com/technetwork/java/javase/downloads/jce-7-download-432124.html). 

## <a name="appropriate-configuration-parameters"></a>Paramètres de Configuration approprié
Pour exécuter le pilote JDBC en mode compatible FIPS, configurez les propriétés de connexion comme indiqué dans le tableau suivant. 

#### <a name="properties"></a>Propriétés 

|Propriété|Type|Valeur par défaut|Description|Remarques|
|---|---|---|---|---|
|encrypt|Booléen [« true / false »]|"false"|Pour FIPS activé JVM chiffrer la propriété doit être **true**||
|TrustServerCertificate|Booléen [« true / false »]|"false"|Pour que FIPS, l’utilisateur doit valider la chaîne de certificats, afin que l’utilisateur doit utiliser **« false »** valeur de cette propriété. ||
|trustStore|String|Null|Votre magasin de clés Java chemin d’accès où vous avez importé votre certificat. Si vous installez le certificat sur votre système, puis pas nécessaire de transmettre quoi que ce soit. Pilote utilise les fichiers cacerts ou jssecacerts.||
|trustStorePassword|String|Null|Mot de passe utilisé pour vérifier l'intégrité des données trustStore.||
|fips|Booléen [« true / false »]|"false"|Pour FIPS activé JVM cette propriété doit être **true**|Ajouté dans 6.1.4 (Stable mise en production 6.2.2)||
|fipsProvider|String|Null|Fournisseur FIPS configuré dans la machine virtuelle Java. Par exemple, BCFIPS ou SunPKCS11-NSS |Ajouté dans 6.1.2 (Stable mise en production 6.2.2), déconseillée dans 6.4.0 - consultez les détails [ici](https://github.com/Microsoft/mssql-jdbc/pull/460).|
|trustStoreType|String|JKS|Type de magasin de confiance FIPS mode jeu PKCS12 ou type défini par le fournisseur FIPS |Ajouté dans 6.1.2 (Stable mise en production 6.2.2)||
| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |
