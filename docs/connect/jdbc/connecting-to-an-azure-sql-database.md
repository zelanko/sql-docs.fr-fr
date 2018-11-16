---
title: Connexion à une base de données SQL Azure | Microsoft Docs
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 49645b1f-39b1-4757-bda1-c51ebc375c34
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c4caaa9ca14fd2f8eb396ef2c2869ba30bd48420
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2018
ms.locfileid: "51602209"
---
# <a name="connecting-to-an-azure-sql-database"></a>Connexion à une base de données SQL Azure

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Cet article aborde les problèmes rencontrés lors de l’utilisation de [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] pour la connexion à [!INCLUDE[ssAzure](../../includes/ssazure_md.md)]. Pour plus d’informations sur la connexion à [!INCLUDE[ssAzure](../../includes/ssazure_md.md)], consultez :  
  
- [Base de données SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview)  
  
- [Guide pratique pour se connecter à SQL Azure avec JDBC](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-java)  

- [Connexion avec l’authentification Azure Active Directory](../../connect/jdbc/connecting-using-azure-active-directory-authentication.md)  
  
## <a name="details"></a>Détails

Lors de la connexion à un [!INCLUDE[ssAzure](../../includes/ssazure_md.md)], vous devez vous connecter à la base de données master pour appeler **SQLServerDatabaseMetaData.getCatalogs**.  
[!INCLUDE[ssAzure](../../includes/ssazure_md.md)] ne prend pas en charge le retour de l’ensemble complet de catalogues d’une base de données utilisateur. **SQLServerDatabaseMetaData.getCatalogs** utiliser la vue sys.databases pour obtenir les catalogues. Reportez-vous à la section autorisations dans [sys.databases (base de données SQL Azure)](https://go.microsoft.com/fwlink/?LinkId=217396) pour comprendre **SQLServerDatabaseMetaData.getCatalogs** comportement sur un [!INCLUDE[ssAzure](../../includes/ssazure_md.md)].  
  
## <a name="connections-dropped"></a>Connexions supprimées

Lors de la connexion à [!INCLUDE[ssAzure](../../includes/ssazure_md.md)], les connexions inactives peuvent être arrêtées par un composant réseau (tel un pare-feu) après une période d'inactivité. Il existe deux types de connexions inactives dans ce contexte :  

- Les connexions inactives sur la couche TCP, lorsque les connexions peuvent être supprimées par n'importe quel dispositif réseau.  

- Les connexions inactives via la passerelle SQL Azure, en cas de messages TCP **keepalive** (qui rendent la connexion non inactive du point de vue de TCP), mais sans requête active pendant 30 minutes. Dans ce scenario, la passerelle détermine que la connexion TDS est inactive à 30 minutes et l'arrête.  
  
Pour éviter la suppression des connexions inactives par un composant réseau, les paramètres de Registre suivants (ou leurs équivalents non Windows) doivent être définis sur le système d'exploitation dans lequel le pilote est chargé&nbsp;:  
  
|Paramètre de Registre|Valeur recommandée|  
|----------------------|-----------------------|  
|HKEY_LOCAL_MACHINE \ SYSTEM \ CurrentControlSet \ Services \ Tcpip \ paramètres \ KeepAliveTime|30 000|  
|HKEY_LOCAL_MACHINE \ SYSTEM \ CurrentControlSet \ Services \ Tcpip \ paramètres \ KeepAliveInterval|1000|  
|HKEY_LOCAL_MACHINE \ SYSTEM \ CurrentControlSet \ Services \ Tcpip \ paramètres \ TcpMaxDataRetransmissions|10|  
  
Redémarrez l’ordinateur pour appliquer les paramètres du Registre.  

Pour effectuer cela lorsque vous exécutez le système dans Windows Azuren, créez une tâche de démarrage pour ajouter les clés de Registre.  Par exemple, ajoutez la tâche de démarrage suivante au fichier de définition du service :  

```xml
<Startup>  
    <Task commandLine="AddKeepAlive.cmd" executionContext="elevated" taskType="simple">  
    </Task>  
</Startup>  
```

Puis ajoutez un fichier AddKeepAlive.cmd à votre projet. Définissez le paramètre « Copier dans le répertoire de sortie » sur « Toujours copier ». Voici un exemple de fichier AddKeepAlive.cmd :  

```bat
if exist keepalive.txt goto done  
time /t > keepalive.txt  
REM Workaround for JDBC keep alive on SQL Azure  
REG ADD HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters /v KeepAliveTime /t REG_DWORD /d 30000 >> keepalive.txt  
REG ADD HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters /v KeepAliveInterval /t REG_DWORD /d 1000 >> keepalive.txt  
REG ADD HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters /v TcpMaxDataRetransmissions /t REG_DWORD /d 10 >> keepalive.txt  
shutdown /r /t 1  
:done  
```

## <a name="appending-the-server-name-to-the-userid-in-the-connection-string"></a>Ajout du nom de serveur à l'ID d'utilisateur dans la chaîne de connexion  

Avant la version 4.0 du [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], lors de la connexion à [!INCLUDE[ssAzure](../../includes/ssazure_md.md)], vous deviez ajouter le nom du serveur à l’ID d’utilisateur dans la chaîne de connexion. Par exemple, user@servername. À compter de la version 4.0 de [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], il n’est plus nécessaire d’ajouter @servername à l’ID d’utilisateur dans la chaîne de connexion.  
  
## <a name="using-encryption-requires-setting-hostnameincertificate"></a>Utilisation du chiffrement, nécessitant la définition d'un hostNameInCertificate

Lors de la connexion à un [!INCLUDE[ssAzure](../../includes/ssazure_md.md)], vous devez spécifier **hostNameInCertificate** si vous spécifiez **chiffrer = true**. (Si le nom du serveur dans la chaîne de connexion est *shortName*. *domainName*, définissez le **hostNameInCertificate** propriété \*. *domainName*.)  
  
Exemple :  

```java
jdbc:sqlserver://abcd.int.mscds.com;databaseName= myDatabase;user=myName;password=myPassword;encrypt=true;hostNameInCertificate= *.int.mscds.com;  
```

## <a name="see-also"></a> Voir aussi

[Connexion à SQL Server avec le pilote JDBC](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)  
