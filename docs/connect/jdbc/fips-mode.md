---
title: Mode FIPS | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: v-nisidh
ms.author: v-nisidh
manager: andrela
ms.openlocfilehash: cc13455e6f56950d6988909b53aa7664c7fd77f3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47723827"
---
# <a name="fips-mode"></a>Mode FIPS
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Microsoft JDBC Driver for SQL Server prend en charge *Mode conforme à FIPS 140*. Pour Oracle / JVM de Sun, reportez-vous à la [Mode conforme à FIPS 140 pour SunJSSE](https://docs.oracle.com/javase/7/docs/technotes/guides/security/jsse/FIPS.html) section fournie par Oracle pour configurer la conformité FIPS activé JVM. 

**Prérequis** :
* FIPS configuré JVM
* Certificat SSL approprié.
* Fichiers de stratégie appropriée. 
* Paramètres de Configuration approprié. 


## <a name="fips-configured-jvm"></a>FIPS configuré JVM

Pour afficher les modules approuvés pour la Configuration de la norme FIPS, reportez-vous à la [validés FIPS 140-1 et les Modules cryptographiques FIPS 140-2](http://csrc.nist.gov/groups/STM/cmvp/documents/140-1/1401val2016.htm). 

Les fournisseurs peuvent avoir des étapes supplémentaires pour configurer JVM avec FIPS.

### <a name="ensure-your-jvm-is-in-fips-mode"></a>Vérifiez que votre machine virtuelle Java est en Mode FIPS
Pour vérifier que votre machine virtuelle Java est FIPS est activés, exécutez l’extrait de code suivant : 

```java
public boolean isFIPS() throws Exception {
    Provider jsse = Security.getProvider("SunJSSE");
    return jsse != null && jsse.getInfo().contains("FIPS");
}
```

## <a name="appropriate-ssl-certificate"></a>Certificat SSL approprié
Pour vous connecter à SQL Server en mode FIPS, un certificat SSL valide est requis. Installer ou importez-le dans le Store de clé Java sur l’ordinateur client (JVM) où FIPS est activé.

### <a name="importing-ssl-certificate-in-java-keystore"></a>L’importation de certificat SSL dans le magasin de clés de Java
Pour FIPS, très probablement vous devez importer le certificat (.cert) soit PKCS ou dans un format spécifique au fournisseur. Utilisez l’extrait de code suivant pour importer le certificat SSL et stockez-le dans un répertoire de travail avec le format de magasin de clés approprié. _TRUST_STORE_PASSWORD_ concerne votre mot de passe KeyStore Java. 

```java
    public void saveGenericKeyStore(String provider, String trustStoreType, String certName, String certPath) throws KeyStoreException, CertificateException, NoSuchAlgorithmException, NoSuchProviderException, IOException {
        KeyStore ks = KeyStore.getInstance(trustStoreType, provider);
        FileOutputStream os = new FileOutputStream("./MyTrustStore_" + trustStoreType);
        ks.load(null, null);
        ks.setCertificateEntry(certName, getCertificate(certPath));
        ks.store(os, TRUST_STORE_PASSWORD.toCharArray());
        os.flush();
        os.close();
    }

    private Certificate getCertificate(String pathName) throws FileNotFoundException, CertificateException {
        FileInputStream fis = new FileInputStream(pathName);
        CertificateFactory cf = CertificateFactory.getInstance("X.509");
        return cf.generateCertificate(fis);
    }

```


L’exemple suivant importe un certificat SSL de Azure au format PKCS12 avec BouncyCastle fournisseur. Le certificat est importé dans le répertoire de travail nommé _MyTrustStore_PKCS12_ à l’aide de l’extrait de code suivant :

` saveGenericKeyStore(BCFIPS, PKCS12, "SQLAzure SSL Certificate Name", "SQLAzure.cer"); `

## <a name="appropriate-policy-files"></a>Fichiers de stratégie appropriée
Pour certains fournisseurs FIPS, les fichiers JAR de stratégie unrestricted sont nécessaires. Dans ce cas, Sun / Oracle, téléchargez les Java Cryptography Extension (JCE) illimité force juridiction stratégie fichiers [JRE 8](http://www.oracle.com/technetwork/java/javase/downloads/jce8-download-2133166.html) ou [JRE 7](http://www.oracle.com/technetwork/java/javase/downloads/jce-7-download-432124.html). 

## <a name="appropriate-configuration-parameters"></a>Paramètres de Configuration approprié
Pour exécuter le pilote JDBC en mode compatible FIPS, configurez les propriétés de connexion comme indiqué dans le tableau suivant. 

**Propriétés** : 

|Propriété|Type|Valeur par défaut|Description|Remarques|
|---|---|---|---|---|
|encrypt|Booléen [« true / false »]|"false"|Pour FIPS activé JVM chiffrer la propriété doit être **true**||
|TrustServerCertificate|Booléen [« true / false »]|"false"|Pour que FIPS, l’utilisateur doit valider la chaîne de certificats, afin que l’utilisateur doit utiliser **« false »** valeur de cette propriété. ||
|trustStore|String|Null|Votre magasin de clés Java chemin d’accès où vous avez importé votre certificat. Si vous installez le certificat sur votre système, puis pas nécessaire de transmettre quoi que ce soit. Pilote utilise les fichiers cacerts ou jssecacerts.||
|trustStorePassword|String|Null|Mot de passe utilisé pour vérifier l'intégrité des données trustStore.||
|fips|Booléen [« true / false »]|"false"|Pour FIPS activé JVM cette propriété doit être **true**|Ajouté dans 6.1.4 (Stable mise en production 6.2.2)||
|fipsProvider|String|Null|Fournisseur FIPS configuré dans la machine virtuelle Java. Par exemple, BCFIPS ou SunPKCS11-NSS |Ajouté dans 6.1.2 (Stable mise en production 6.2.2), déconseillée dans 6.4.0 - consultez les détails [ici](https://github.com/Microsoft/mssql-jdbc/pull/460).|
|trustStoreType|String|JKS|Type de magasin de confiance FIPS mode jeu PKCS12 ou type défini par le fournisseur FIPS |Ajouté dans 6.1.2 (Stable mise en production 6.2.2)||



  
