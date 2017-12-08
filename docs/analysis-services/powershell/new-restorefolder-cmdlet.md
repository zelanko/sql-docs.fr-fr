---
title: Applet de commande New-RestoreFolder | Documents Microsoft
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
ms.assetid: 5938b3a9-6412-45fc-86f8-264651d01598
caps.latest.revision: "10"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f6bf2b5e2d63c5ad3e63c6a5393f83d438192ed6
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="new-restorefolder-cmdlet"></a>Applet de commande New-RestoreFolder

[!INCLUDE[ssas-appliesto-sqlas-all](../../includes/ssas-appliesto-sqlas-all.md)]

  Restaure un dossier d'origine vers un nouveau dossier.  

>[!NOTE] 
>Cet article peut contenir des exemples et des informations obsolètes. Utilisez l’applet de commande Get-Help pour la dernière version.
  
## <a name="syntax"></a>Syntaxe  
 `New-RestoreFolder [-OriginalFolder] <String> [-NewFolder] <String> [-AsTemplate] [-Server <String>] [-Credential <PSCredential>] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]`  
  
 `New-RestoreFolder [-Server <String>] [-Credential <PSCredential>] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]`  
  
 Les paramètres communs, tels que –Verbose et -Debug, ainsi que les paramètres d'erreur et d'avertissement, -Whatif et –Confirm, sont décrits dans la référence Windows PowerShell. Pour plus d’informations, consultez [about_CommonParameters](http://technet.microsoft.com/library/dd315352.aspx).  
  
## <a name="description"></a>Description  
 L'applet de commande New-RestoreFolder est utilisée pour créer un dossier en fonction du nom du dossier d'origine.  
  
## <a name="parameters"></a>Paramètres  
  
### <a name="-originalfolder-string"></a>-OriginalFolder \<chaîne >  
 Obtient l'emplacement du dossier d'origine.  
  
|||  
|-|-|  
|Requis ?|true|  
|Position ?|0|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|true|  
|Accepter les caractères génériques ?|false|  
  
### <a name="-newfolder-string"></a>-NewFolder \<chaîne >  
 Définit l'emplacement d'un nouveau dossier.  
  
|||  
|-|-|  
|Requis ?|true|  
|Position ?|1|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|true|  
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
|Entrées||  
|Sorties|Aucune|  
  
