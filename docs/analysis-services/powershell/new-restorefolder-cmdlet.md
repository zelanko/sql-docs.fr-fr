---
title: "Applet de commande New-RestoreFolder | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 5938b3a9-6412-45fc-86f8-264651d01598
caps.latest.revision: 10
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 10
---
# Applet de commande New-RestoreFolder
  Restaure un dossier d'origine vers un nouveau dossier.  
  
## Syntaxe  
 `New-RestoreFolder [-OriginalFolder] <String> [-NewFolder] <String> [-AsTemplate] [-Server <String>] [-Credential <PSCredential>] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]`  
  
 `New-RestoreFolder [-Server <String>] [-Credential <PSCredential>] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]`  
  
 Les paramètres communs, tels que –Verbose et -Debug, ainsi que les paramètres d'erreur et d'avertissement, -Whatif et –Confirm, sont décrits dans la référence Windows PowerShell. Pour plus d’informations, consultez [about_CommonParameters](http://technet.microsoft.com/library/dd315352.aspx).  
  
## Description  
 L'applet de commande New-RestoreFolder est utilisée pour créer un dossier en fonction du nom du dossier d'origine.  
  
## Paramètres  
  
### -OriginalFolder \<string>  
 Obtient l'emplacement du dossier d'origine.  
  
|||  
|-|-|  
|Requis ?|true|  
|Position ?|0|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|true|  
|Accepter les caractères génériques ?|false|  
  
### -NewFolder \<string>  
 Définit l'emplacement d'un nouveau dossier.  
  
|||  
|-|-|  
|Requis ?|true|  
|Position ?|1|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|true|  
|Accepter les caractères génériques ?|false|  
  
### -AsTemplate \<SwitchParameter>  
 Spécifie si l'objet doit être créé en mémoire et retourné.  
  
|||  
|-|-|  
|Requis ?|false|  
|Position ?|nommée|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### -Server \<string>  
 Spécifie l'instance Analysis Services à laquelle l'applet de commande se connectera et qu'il exécutera. Si aucun nom de serveur n'est fourni, une connexion sera établie à localhost. Pour les instances par défaut, spécifiez simplement le nom du serveur. Pour les instances nommées, utilisez le format nom_serveur\nom_instance. Pour les connexions HTTP, utilisez le format http[s]://serveur[:port]/répertoirevirtuel/msmdpump.dll.  
  
|||  
|-|-|  
|Requis ?|false|  
|Position ?|nommée|  
|Valeur par défaut|localhost|  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### -Credential \<PSCredential>  
 Ce paramètre est utilisé pour transmettre un nom d'utilisateur et un mot de passe lors de l'utilisation d'une connexion HTTP à une instance Analysis Services, pour une instance que vous avez configurée pour l'accès HTTP. Pour plus d’informations, consultez [Configurer l’accès HTTP à Analysis Services sur Internet Information Services &#40;IIS&#41; 8.0](../../analysis-services/instances/configure http access to analysis services on iis 8.0.md) et [Scripts PowerShell dans Analysis Services](../../analysis-services/instances/powershell-scripting-in-analysis-services.md) pour les connexions HTTP.  
  
 Si ce paramètre est indiqué, le nom d'utilisateur et le mot de passe seront utilisés pour la connexion à l'instance du serveur d'analyse spécifiée. Si aucune information d'identification n'est indiquée, le compte Windows par défaut de l'utilisateur qui exécute l'outil sera utilisé.  
  
 Pour utiliser ce paramètre, créez d’abord un objet PSCredential à l’aide de Get-Credential pour spécifier le nom d’utilisateur et le mot de passe, par exemple, `$Cred=Get-Credential “adventure-works\bobh”`. Vous pouvez ensuite canaliser cet objet vers le paramètre –Credential `(-Credential:$Cred`).  
  
|||  
|-|-|  
|Requis ?|false|  
|Position ?|nommée|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|True (ByValue)|  
|Accepter les caractères génériques ?|false|  
  
## Entrées et sorties  
 Le type d'entrée correspond au type des objets que vous pouvez canaliser vers l'applet de commande. Le type de retour correspond au type des objets retournés par l'applet de commande.  
  
|||  
|-|-|  
|Entrées||  
|Sorties|Aucun|  
  
## Exemples  
  
## Voir aussi  
 [PowerShell scripting in Analysis Services](../../analysis-services/instances/powershell-scripting-in-analysis-services.md)   
 [Gérer les modèles tabulaires à l'aide de PowerShell](http://go.microsoft.com/fwlink/?linkID=227685)  
  
  