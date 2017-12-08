---
title: Applet de commande New-RestoreLocation | Documents Microsoft
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: powershell
ms.reviewer: 
ms.suite: sql
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 5ca13d8c-1c5d-4f02-869c-72e0defce6d7
caps.latest.revision: "11"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 11b5d0bd210d80698706751a3734f2e96810187e
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="new-restorelocation-cmdlet"></a>Applet de commande New-RestoreLocation

[!INCLUDE[ssas-appliesto-sqlas-all](../../includes/ssas-appliesto-sqlas-all.md)]

  Spécifie les informations utilisées pour restaurer une base de données.  

>[!NOTE] 
>Cet article peut contenir des exemples et des informations obsolètes. Utilisez l’applet de commande Get-Help pour la dernière version.
  
## <a name="syntax"></a>Syntaxe  
 `New-RestoreLocation [-File <String>] [-DataSourceId <String>] [-ConnectionString <String>] [-DataSourceType <RestoreDataSourceType>] [-Folders <RestoreFolder[]>] [-AsTemplate] [-Server <String>] [-Credential <PSCredential>] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]`  
  
 `New-RestoreLocation [-Server <String>] [-Credential <PSCredential>] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]`  
  
 Les paramètres communs, tels que –Verbose et -Debug, ainsi que les paramètres d'erreur et d'avertissement, -Whatif et –Confirm, sont décrits dans la référence Windows PowerShell. Pour plus d’informations, consultez [about_CommonParameters](http://technet.microsoft.com/library/dd315352.aspx).  
  
## <a name="description"></a>Description  
 L'applet de commande New-RestoreLocation contient les informations utilisées pour restaurer une base de données, y compris la chaîne de connexion du serveur et de la base de données, des propriétés de la source de données, des fichiers et dossiers associés à la base de données qui est restaurée.  
  
## <a name="parameters"></a>Paramètres  
  
### <a name="-file-string"></a>-Fichier \<chaîne >  
 Spécifie le nom du fichier de sauvegarde que vous restaurez.  
  
|||  
|-|-|  
|Requis ?|false|  
|Position ?|nommée|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### <a name="-datasourceid-string"></a>-DataSourceId \<chaîne >  
  
|||  
|-|-|  
|Requis ?|false|  
|Position ?|nommée|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### <a name="-connectionstring-string"></a>-ConnectionString \<chaîne >  
 Spécifie la chaîne de connexion d'une instance Analysis Services distante.  
  
|||  
|-|-|  
|Requis ?|false|  
|Position ?|nommée|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### <a name="-datasourcetype-asrestoredatasourcetype"></a>-DataSourceType \<As. RestoreDataSourceType >  
 Spécifie si la source de données est distante ou locale, selon l'emplacement de la partition.  
  
|||  
|-|-|  
|Requis ?|false|  
|Position ?|nommée|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### <a name="-folders-asrestorefolder"></a>-Dossiers \<As. RestoreFolder >  
 Spécifie des dossiers de partitions sur l'instance locale ou distante.  
  
|||  
|-|-|  
|Requis ?|false|  
|Position ?|nommée|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### <a name="-astemplate-switchparameter"></a>-AsTemplate \<Paramètre_booléen >  
 Spécifie si l'objet doit être créé en mémoire et retourné.  
  
|||  
|-|-|  
|Requis ?|false|  
|Position ?|nommée|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### <a name="-server-string"></a>-Serveur \<chaîne >  
 Spécifie l'instance Analysis Services à laquelle l'applet de commande se connectera et qu'il exécutera. Si aucun nom de serveur n'est fourni, une connexion sera établie à localhost. Pour les instances par défaut, spécifiez simplement le nom du serveur. Pour les instances nommées, utilisez le format nom_serveur\nom_instance. Pour les connexions HTTP, utilisez le format http[s]://serveur[:port]/répertoirevirtuel/msmdpump.dll.  
  
|||  
|-|-|  
|Requis ?|false|  
|Position ?|nommée|  
|Valeur par défaut|localhost|  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### <a name="-credential-pscredential"></a>-Credential \<PSCredential >  
 Ce paramètre est utilisé pour transmettre un nom d'utilisateur et un mot de passe lors de l'utilisation d'une connexion HTTP à une instance Analysis Services, pour une instance que vous avez configurée pour l'accès HTTP. Pour plus d’informations, consultez [configurer l’accès HTTP à Analysis Services sur Internet Information Services &#40; IIS &#41; 8.0](../../analysis-services/instances/configure-http-access-to-analysis-services-on-iis-8-0.md) pour les connexions HTTP.  
  
 Si ce paramètre est indiqué, le nom d'utilisateur et le mot de passe seront utilisés pour la connexion à l'instance du serveur d'analyse spécifiée. Si aucune information d'identification n'est indiquée, le compte Windows par défaut de l'utilisateur qui exécute l'outil sera utilisé.  
  
 Pour utiliser ce paramètre, créez d’abord un objet PSCredential à l’aide de Get-Credential pour spécifier le nom d’utilisateur et le mot de passe (par exemple, `$Cred=Get-Credential “adventure-works\bobh”`. Vous pouvez ensuite canaliser cet objet vers le paramètre –Credential `(-Credential:$Cred`).  
  
|||  
|-|-|  
|Requis ?|false|  
|Position ?|nommée|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|True (ByValue)|  
|Accepter les caractères génériques ?|false|  
  
## <a name="inputs-and-outputs"></a>Entrées et sorties  
 Le type d'entrée correspond au type des objets que vous pouvez canaliser vers l'applet de commande. Le type de retour correspond au type des objets retournés par l'applet de commande.  
  
|||  
|-|-|  
|Entrées|Aucun|  
|Sorties|Aucun|  
  
## <a name="examples"></a>Exemples  
  
  
