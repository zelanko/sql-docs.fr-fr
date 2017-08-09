---
title: "Méthode de SetDatabaseConnection (WMI MSReportServer_ConfigurationSetting) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SetDatabaseConnection (WMI MSReportServer_ConfigurationSetting Class)
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- SetDatabaseConnection method
ms.assetid: c040aa78-92b8-41e4-9ae2-eff9fcdddc5b
caps.latest.revision: 19
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: c5e64ee5fa73b98d30797142ed6a3ed8f080bcb0
ms.contentlocale: fr-fr
ms.lasthandoff: 08/09/2017

---
# <a name="configurationsetting-method---setdatabaseconnection"></a>Méthode ConfigurationSetting - SetDatabaseConnection
  Définit la connexion à une base de données de serveur de rapports spécifique.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Public Sub SetDatabaseConnection(Server as String, _  
    DatabaseName as string, CredentialsType as Integer, _  
    Username as String, Password as String, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void BackupEncryptionKey(string Server,   
    string DatabaseName, Int32 CredentialsType,   
    string UserName, string Password, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Paramètres  
 *Server*  
 Nom de l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisée pour héberger la base de données du serveur de rapports.  
  
 *DatabaseName*  
 Nom de la base de données du serveur de rapports.  
  
 *CredentialsType*  
 Type d'informations d'identification à utiliser pour la connexion. Les valeurs peuvent être les suivantes :  
  
-   0 - Windows  
  
-   1 – [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   2 - Service Windows  
  
 *UserName*  
 Nom du compte utilisé pour établir la connexion à la base de données du serveur de rapports.  
  
 *Mot de passe*  
 Mot de passe utilisé pour établir la connexion à la base de données du serveur de rapports.  
  
 *HRESULT*  
 [out] Valeur indiquant si l'appel a réussi ou échoué.  
  
## <a name="return-value"></a>Valeur retournée  
 Retourne un paramètre *HRESULT* qui indique si l'appel de la méthode a réussi ou a échoué. Une valeur 0 indique que l'appel de méthode a réussi. Une valeur différente de zéro indique qu'une erreur s'est produite.  
  
## <a name="remarks"></a>Notes  
 Quand le paramètre *CredentialsType* a la valeur 0 (Windows), les paramètres *UserName* et *Password* doivent être définis. Le paramètre *UserName* doit être au format « domaine\nom utilisateur », et la valeur doit représenter une ouverture de session Windows valide.  
  
 Quand le paramètre *CredentialsType* a la valeur 1 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]), la valeur transmise dans le paramètre *UserName* doit être conforme aux spécifications d’un nom de connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Quand le paramètre *CredentialsType* a la valeur 2 (Service Windows), le serveur de rapports utilise la sécurité intégrée pour se connecter à la base de données du serveur de rapports, et les paramètres *UserName* et *Password* sont ignorés. Le service Web Report Server utilise soit le compte [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] , soit le compte d’un pool d’applications et le compte de service Windows pour accéder à la base de données du serveur de rapports.  
  
 Quand la méthode SetDatabaseConnection est appelée, elle chiffre et stocke les informations d’identification et les informations sur la base de données dans le fichier de configuration du serveur de rapports spécifié.  
  
 La méthode SetDatabaseConnection ne vérifie pas si le serveur de rapports peut se connecter à la base de données à l’aide des données spécifiées.  
  
 Quand elle est configurée pour la première fois, la propriété ConnectionPoolSize est définie selon les processeurs suivants : ConnectionPoolSize = #Processors * 75.  
  
 La méthode SetDatabaseConnection n’accorde pas d’autorisations aux comptes spécifiés. Vous devez appeler la méthode [GenerateDatabaseRightsScript](../../reporting-services/wmi-provider-library-reference/configurationsetting-method-generatedatabaserightsscript.md) pour chaque compte qui doit accéder à la base de données du serveur de rapports et exécuter le script obtenu.  
  
## <a name="requirements"></a>Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
