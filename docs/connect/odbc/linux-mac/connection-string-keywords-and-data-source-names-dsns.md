---
title: Connexion à SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data source names
- connection string keywords
- DSNs
ms.assetid: f95cdbce-e7c2-4e56-a9f7-8fa3a920a125
caps.latest.revision: 41
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 878a88fac188f23f48c25fdc54fec7540a9b6771
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2018
ms.locfileid: "38982311"
---
# <a name="connecting-to-sql-server"></a>Connexion à SQL Server
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Cette rubrique explique comment créer une connexion à une base de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].  
  
## <a name="connection-properties"></a>Propriétés de connexion  

Consultez [DSN et les mots clés de chaîne de connexion et les attributs](../../../connect/odbc/dsn-connection-string-attribute.md) pour tous les mots clés de chaîne de connexion et les attributs pris en charge sur Mac et Linux

> [!IMPORTANT]  
> Quand vous vous connectez à une base de données qui utilise la mise en miroir de bases de données (qui a un partenaire de basculement), ne spécifiez pas le nom de la base de données dans la chaîne de connexion. Envoyez plutôt une commande **use***database_name* pour vous connecter à la base de données avant l’exécution de vos requêtes.  
  
La valeur passée à la **pilote** mot clé peut prendre l’une des opérations suivantes :  
  
-   le nom que vous avez utilisé quand vous avez installé le pilote,

-   le chemin de la bibliothèque du pilote, spécifié dans le fichier .ini du modèle utilisé pour installer le pilote.  

Pour créer un DSN, créer (si nécessaire) et modifiez le fichier **~/.odbc.ini** (`.odbc.ini` dans votre répertoire de base) pour un DSN utilisateur accessible uniquement à l’utilisateur actuel, ou `/etc/odbc.ini` pour une source de données système (des privilèges d’administrateur requis.) Voici un exemple de fichier qui montre les entrées exigées pour un nom de source de données :  

```  
[MSSQLTest]  
Driver = ODBC Driver 13 for SQL Server  
Server = [protocol:]server[,port]  
#   
# Note:  
# Port is not a valid keyword in the odbc.ini file  
# for the Microsoft ODBC driver on Linux or macOS
#  
```  

Vous pouvez éventuellement spécifier le protocole et le port à connecter au serveur. Par exemple, **Server = tcp :***nom_serveur***, 12345**. Notez que le seul protocole pris en charge par les pilotes Linux et macOS est `tcp`.

Pour vous connecter à une instance nommée sur un port statique, utilisez <b>Server=</b>*servername*,**port_number**. La connexion à un port dynamique n’est pas prise en charge.  

Éventuellement, vous pouvez ajouter les informations de nom de source de données à un fichier de modèle, puis exécuter la commande suivante pour l’ajouter à `~/.odbc.ini` :
 - **ODBCINST -i --s-f** *template_file*  
 
Vous pouvez vérifier que votre pilote fonctionne à l’aide de `isql` pour tester la connexion, ou vous pouvez utiliser cette commande :
 - **master.INFORMATION_SCHEMA.TABLES bcp out -S de fichier OutFile.dat <server> - U <name> - P <password>**  

## <a name="using-secure-sockets-layer-ssl"></a>Utilisation du protocole SSL (Secure Sockets Layer)  
Vous pouvez utiliser le protocole SSL (Secure Sockets Layer) pour chiffrer les connexions à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]. Le protocole SSL protège les noms d’utilisateur et mots de passe [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] sur le réseau. Il vérifie également l’identité du serveur à des fins de protection contre les attaques de l’intercepteur (« man in the middle »).  

L’activation du chiffrement renforce la sécurité au détriment des performances.

Pour plus d’informations, consultez [chiffrement des connexions à SQL Server](http://go.microsoft.com/fwlink/?LinkId=220900) et [à l’aide du chiffrement sans Validation](https://docs.microsoft.com/sql/relational-databases/native-client/features/using-encryption-without-validation).

Quels que soient les paramètres pour **Encrypt** et **TrustServerCertificate**, les informations d’identification de connexion serveur (nom d’utilisateur et mot de passe) sont toujours chiffrées. Le tableau suivant montre l’effet des paramètres **Encrypt** et **TrustServerCertificate** .  

||**TrustServerCertificate = non**|**TrustServerCertificate = yes**|  
|-|-------------------------------------|------------------------------------|  
|**Encrypt=no**|Le certificat de serveur n’est pas vérifié.<br /><br />Les données envoyées entre le client et le serveur ne sont pas chiffrées.|Le certificat de serveur n’est pas vérifié.<br /><br />Les données envoyées entre le client et le serveur ne sont pas chiffrées.|  
|**Encrypt=yes**|Le certificat de serveur est vérifié.<br /><br />Les données envoyées entre le client et le serveur sont chiffrées.<br /><br />Le nom (ou l’adresse IP) indiqué dans un nom commun de l’objet ou autre nom de l’objet dans un certificat SSL [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] doit correspondre exactement au nom (ou à l’adresse IP) du serveur spécifié dans la chaîne de connexion.|Le certificat de serveur n’est pas vérifié.<br /><br />Les données envoyées entre le client et le serveur sont chiffrées.|  

Par défaut, les connexions chiffrées vérifient toujours le certificat du serveur. Toutefois, si vous vous connectez à un serveur qui dispose d’un certificat auto-signé, également ajouter le `TrustServerCertificate` possibilité de contourner la vérification du certificat à la liste des autorités de certification approuvées :  

```  
Driver={ODBC Driver 13 for SQL Server};Server=ServerNameHere;Encrypt=YES;TrustServerCertificate=YES  
```  
  
Le protocole SSL utilise la bibliothèque OpenSSL. Le tableau suivant présente les versions minimales prises en charge d’OpenSSL et les emplacements du magasin d’approbations de certificat par défaut pour chaque plateforme :

|Plateforme|Version OpenSSL minimale|Emplacement du magasin d’approbations de certificat par défaut|  
|------------|---------------------------|--------------------------------------------|
|Debian 9|1.1.0|/etc/ssl/certs|
|8.71 Debian |1.0.1|/etc/ssl/certs|
|macOS 10.13|1.0.2|/usr/local/etc/OpenSSL/Certs|
|macOS 10.12|1.0.2|/usr/local/etc/OpenSSL/Certs|
|OS X 10.11|1.0.2|/usr/local/etc/OpenSSL/Certs|
|Red Hat Enterprise Linux 7|1.0.1|/etc/pki/tls/cert.pem|
|Red Hat Enterprise Linux 6|1.0.0-10|/etc/pki/tls/cert.pem|
|SUSE Linux Enterprise 12 |1.0.1|/etc/ssl/certs|
|SUSE Linux Enterprise 11 |0.9.8|/etc/ssl/certs|
|Ubuntu 17.10 |1.0.2|/etc/ssl/certs|
|Ubuntu 16.10 |1.0.2|/etc/ssl/certs|
|Ubuntu 16.04 |1.0.2|/etc/ssl/certs|
  
Vous pouvez également spécifier le chiffrement dans la chaîne de connexion en utilisant le `Encrypt` option lors de l’utilisation **SQLDriverConnect** pour vous connecter.

## <a name="see-also"></a> Voir aussi  
[Installation de Microsoft ODBC Driver for SQL Server sur Linux et macOS](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)  
[Instructions de programmation](../../../connect/odbc/linux-mac/programming-guidelines.md)
