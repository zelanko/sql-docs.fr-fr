---
title: "Chiffrement des connexions à SQL Server sur Linux | Documents Microsoft"
description: "Cette rubrique décrit le chiffrement des connexions à SQL Server sur Linux."
author: tmullaney
ms.date: 06/14/2017
ms.author: thmullan;rickbyh
manager: jhubbard
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 
helpviewer_keywords:
- Linux, encrypted connections
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: dfbfeee8292f3af4020185248d3d6a3fad3c71ea
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="encrypting-connections-to-sql-server-on-linux"></a>Chiffrement des connexions à SQL Server sur Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../../docs/includes/tsql-appliesto-sslinux-only.md)]

[!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)]sur Linux peuvent utiliser sécurité TLS (Transport Layer) pour chiffrer les données transmises sur un réseau entre une application cliente et une instance de [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)]prend en charge les mêmes protocoles TLS sur Windows et Linux : TLS 1.0, 1.1 et 1.2. Toutefois, les étapes de configuration TLS sont spécifiques au système d’exploitation sur lequel [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] est en cours d’exécution.  
 
## <a name="typical-scenario"></a>Scénario typique 
TLS est utilisé pour chiffrer les connexions à partir d’une application cliente [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)]. En cas de correctement configuré, TLS fournit la confidentialité et l’intégrité des données pour les communications entre le client et le serveur.  
Les étapes suivantes décrivent un scénario classique :  

1. Administrateur de base de données génère une clé privée et un certificat (CSR) de demande de signature. Nom commun du conseiller du service clientèle doit correspondre au nom de serveur qui spécifient des clients dans leur chaîne de connexion SQL Server. Ce nom commun est généralement le nom de domaine complet de le [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] hôte. Pour utiliser le même certificat pour plusieurs serveurs, vous pouvez utiliser un caractère générique dans le nom commun (par exemple, `"*.contoso.com"` au lieu de `"node1.contoso.com"`).   
2. La signature de certificat est envoyé à une autorité de certification (CA) pour la signature. L’autorité de certification doit être approuvée par tous les ordinateurs clients qui se connectent à [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)]. L’autorité de certification renvoie un certificat signé à l’administrateur de base de données.   
3. Administrateur de base de données configure [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] à utiliser la clé privée et le certificat signé pour les connexions TLS.   
4. Les clients spécifier `"Encrypt=True"` et `"TrustServerCertificate=False"` dans leurs chaînes de connexion. (Les noms de paramètre spécifique peuvent être différentes selon le pilote est utilisé). Les clients essaient de maintenant chiffrer les connexions à SQL Server et vérifier la validité du certificat du serveur SQL pour empêcher les attaques de man-in-the-middle.  
 
## <a name="configuring-tls-on-linux"></a>Configuration du protocole TLS sur Linux  

Utilisez `mssql-conf` pour configurer le protocole TLS pour une instance de [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] en cours d’exécution sur Linux. Les options suivantes sont prises en charge :  

|Option | Description |
|--- |--- |
|`network.forceencryption` |La valeur 1, puis [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] force toutes les connexions à chiffrer. Par défaut, cette option est 0. |  
|`network.tlscert` |Le chemin d’accès absolu pour le certificat du fichier qui [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] utilise pour TLS. Exemple : `/etc/ssl/certs/mssql.pem` le fichier de certificat doit être accessible par le compte mssql. Microsoft vous recommande de restreindre l’accès au fichier à l’aide de `chown mssql:mssql <file>; chmod 400 <file>`. |  
|`network.tlskey` |Le chemin d’accès absolu à la clé privée du fichier qui [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] utilise pour TLS. Exemple : `/etc/ssl/private/mssql.key` le fichier de certificat doit être accessible par le compte mssql. Microsoft vous recommande de restreindre l’accès au fichier à l’aide de `chown mssql:mssql <file>; chmod 400 <file>`. | 
|`network.tlsprotocols` |Une liste séparée par des virgules de quels TLS protocoles sont autorisés par SQL Server. [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)]tente toujours de négocier le protocole autorisé les plus fortes. Si un client ne prend pas en charge n’importe quel protocole autorisé, [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] rejette la tentative de connexion.  Pour la compatibilité, tous les protocoles pris en charge sont autorisés par défaut (1.2, 1.1, 1.0).  Si vos clients prennent en charge TLS 1.2, Microsoft vous recommande d’autoriser uniquement TLS 1.2. |  
|`network.tlsciphers` |Spécifie les chiffrements autorisés par [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] pour TLS. Cette chaîne doit être mise en forme par [format de liste de chiffrement d’OpenSSL](https://www.openssl.org/docs/man1.0.2/apps/ciphers.html). En règle générale, vous ne devez pas modifier cette option. <br /> Par défaut, les chiffrements suivants sont autorisés : <br /> `ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES128-SHA256:ECDHE-ECDSA-AES256-SHA384:ECDHE-RSA-AES128-SHA256:ECDHE-RSA-AES256-SHA384:ECDHE-ECDSA-AES256-SHA:ECDHE-ECDSA-AES128-SHA:ECDHE-RSA-AES256-SHA:ECDHE-RSA-AES128-SHA:AES256-GCM-SHA384:AES128-GCM-SHA256:AES256-SHA256:AES128-SHA256:AES256-SHA:AES128-SHA` |   
| | |
 
## <a name="example"></a>Exemple 
Cet exemple utilise un certificat auto-signé. Dans les scénarios de production normale, le certificat serait être signé par une autorité de certification approuvée par tous les clients.  
 
### <a name="step-1-generate-private-key-and-certificate"></a>Étape 1 : Générer le certificat et la clé privée 
Ouvrez une commande de Terminal Server sur l’ordinateur Linux où [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] est en cours d’exécution. Exécutez les commandes suivantes :  

- Générez un certificat auto-signé. Assurez-vous que le CN correspond à votre nom de domaine complet d’hôte SQL Server. Vous pouvez éventuellement utiliser des caractères génériques, par exemple `'/CN=*.contoso.com'`.    
   ```  
   openssl req -x509 -nodes -newkey rsa:2048 -subj '/CN=mssql.contoso.com' -keyout mssql.key -out mssql.pem -days 365 
   ```  

- Restreindre l’accès à`mssql`  
   ```  
   sudo chown mssql:mssql mssql.pem mssql.key 
   sudo chmod 400 mssql.pem mssql.key 
   ```  
 
- Déplacer vers les répertoires du système SSL (facultatifs)  
   ```  
   sudo mv mssql.pem /etc/ssl/certs/ 
   sudo mv mssql.key /etc/ssl/private/ 
   ```  
 
### <a name="step-2-configure--includessnoversiondocsincludesssnoversion-mdmd"></a>Étape 2 : configurer[!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)]  
Utilisez `mssql-conf` pour configurer [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] pour utiliser le certificat et la clé pour le protocole TLS. Pour une sécurité accrue, vous pouvez également définir TLS 1.2 comme le seul protocole autorisé et forcer les clients à utiliser des connexions chiffrées.  

```  
sudo /opt/mssql/bin/mssql-conf set network.tlscert /etc/ssl/certs/mssql.pem 
sudo /opt/mssql/bin/mssql-conf set network.tlskey /etc/ssl/private/mssql.key 
sudo /opt/mssql/bin/mssql-conf set network.tlsprotocols 1.2 
sudo /opt/mssql/bin/mssql-conf set network.forceencryption 1 
```
 
### <a name="step-3-restart-includessnoversiondocsincludesssnoversion-mdmd"></a>Étape 3 : redémarrer[!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] 
[!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)]doit être redémarré pour que ces modifications prennent effet.  
`sudo systemctl restart mssql-server`  
 
### <a name="step-4-copy-self-signed-certificate-to-client-machines"></a>Étape 4 : Copie le certificat auto-signé pour les ordinateurs clients 
Étant donné que cet exemple utilise un certificat auto-signé par le [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] hôte, le certificat (pas la clé privée) doit être copié et installé comme certificat racine approuvé sur tous les ordinateurs clients qui se connectent à [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)]. Si le certificat est signé par une autorité de certification déjà approuvée par tous les clients, cette étape n’est pas nécessaire. 
 
### <a name="step-5-connect-from-clients-using-tls"></a>Étape 5 : Se connecter à partir de clients à l’aide de TLS 
Se connecter à [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] à partir d’un client avec le chiffrement activé et `TrustServerCertificate` la valeur `False` dans la chaîne de connexion. Voici quelques exemples montrant comment spécifier ces paramètres à l’aide de différents outils et des pilotes. 

sqlcmd  
`sqlcmd -N -C -S mssql.contoso.com -U sa -P '<YourPassword>'`  

[!INCLUDE[ssmanstudiofull-md](../../docs/includes/ssmanstudiofull-md.md)]   
  ![Boîte de dialogue de connexion SSMS](media/sql-server-linux-encrypted-connections/ssms-encrypt-connection.png "boîte de dialogue de connexion SSMS")  
  
ADO.NET  
`"Encrypt=true; TrustServerCertificate=true;"`  

ODBC   
`"Encrypt=yes; TrustServerCertificate=no;"`  

JDBC  
`"encrypt=true; trustServerCertificate=false;" `

 
## <a name="common-connection-errors"></a>Erreurs de connexion courantes  

|Message d'erreur |Fix |
|--- |--- |
|La chaîne de certificats a été émise par une autorité qui n’est pas approuvée.  |Cette erreur se produit lorsque les clients ne peuvent pas vérifier la signature sur le certificat présenté par SQL Server pendant la négociation TLS. Assurez-vous que le client approuve soit le [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] certificat directement, ou l’autorité de certification qui a signé le certificat SQL Server. |
|Le nom du principal cible est incorrect.  |Vérifiez que champ de nom commun de certificat SQL Server correspond au nom de serveur spécifié dans la chaîne de connexion du client. |  
|Une connexion existante a dû être fermée par l’hôte distant. |Cette erreur peut se produire lorsque le client ne prend pas en charge la version du protocole TLS requise par SQL Server. Par exemple, si [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] est configuré pour exiger le protocole TLS 1.2, assurez-vous que vos clients prennent également en charge le protocole TLS 1.2. |
| | |   


