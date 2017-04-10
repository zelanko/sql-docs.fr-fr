---
title: "Applet de commande Add-RoleMember | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 827c8bbc-d48f-4e49-9ea5-abb1380f7623
caps.latest.revision: 14
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 14
---
# Applet de commande Add-RoleMember
  Ajoutez un membre au rôle spécifié d'une base de données multidimensionnelle ou tabulaire Analysis Services.  
  
## Syntaxe  
 `Add-RoleMember [-MemberName] <System.String> [-Database] <System.String> [-RoleName] <System.String> [<CommonParameters>]`  
  
 `Add-RoleMember [-MemberName] <System.String> [-DatabaseRole] <Microsoft.AnalysisServices.Role> [<CommonParameters>]`  
  
## Description  
 L'applet de commande Add-RoleMember ajoute un membre valide à un rôle de base de données existant. Seuls les rôles de base de données sont autorisés. Vous ne pouvez pas utiliser cet applet de commande pour ajouter des membres à un rôle serveur.  
  
 Vous pouvez uniquement ajouter un membre à la fois, qui peut être un compte d'utilisateur ou de groupe.  
  
## Paramètres  
  
### -MemberName \<chaîne>  
 Spécifie l'utilisateur ou le groupe Windows à ajouter au rôle.  
  
|||  
|-|-|  
|Requis ?|true|  
|Position ?|0|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### -Database \<chaîne>  
 Spécifie la base de données à laquelle le rôle appartient.  
  
|||  
|-|-|  
|Requis ?|true|  
|Position ?|1|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### -RoleName \<chaîne>  
 Spécifie le rôle auquel vous ajoutez des membres.  
  
|||  
|-|-|  
|Requis ?|true|  
|Position ?|2|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### -DatabaseRole \<chaîne>  
 Spécifie l'objet Microsoft.AnalysisServices.Role auquel le membre doit être ajouté. Utilisez ce paramètre comme une alternative aux paramètres –Database et –RoleName, lorsque vous souhaitez fournir le rôle de base de données via le pipeline.  
  
|||  
|-|-|  
|Requis ?|true|  
|Position ?|nommée|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|true (ByPropertyName)|  
|Accepter les caractères génériques ?|false|  
  
### \<CommonParameters>  
 La commande cmdlet prend en charge les paramètres communs : -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer et -OutVariable. Pour plus d’informations, consultez [About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## Entrées et sorties  
 Le type d'entrée correspond au type des objets que vous pouvez canaliser vers l'applet de commande. Le type de retour correspond au type des objets retournés par l'applet de commande.  
  
|||  
|-|-|  
|Entrées|Aucun.|  
|Sorties|Aucun|  
  
## Exemple 1  
  
```  
PS SQLSERVER:\sqlas\localhost\default> add-rolemember –membername “adventure-works\bobh” –database “AdventureWorks” –rolename “Reader”  
```  
  
 Cette commande ajoute un compte d'utilisateur de domaine Windows au rôle Lecteur pour la base de données AdventureWorks exécutée sur une instance par défaut locale.  
  
## Exemple 2  
  
```  
PS SQLSERVER:\sqlas\localhost\default> $roles= dir .\databases\AWTEST\Roles  
PS SQLSERVER:\sqlas\localhost\default> $roles  
PS SQLSERVER:\sqlas\localhost\default> add-rolemember –membername:“adventure-works\bobh” –databaserole:$roles[0]  
```  
  
 La ligne 1 ajoute tous les rôles de la base de données AWTEST au pipeline. La ligne 2, où vous tapez $roles à l'invite, affiche le tableau de rôles. La ligne 3 ajoute l'utilisateur Windows adventure-works\bobh en tant que membre du premier rôle dans le tableau.  
  
## Exemple 3  
  
```  
PS SQLSERVER:\sqlas\localhost\default\Databases\AWTEST\Roles> $roles=dir  
PS SQLSERVER:\sqlas\localhost\default\Databases\AWTEST\Roles> $roles[0] | Add-rolemember –membername “adventure-works\bobh”  
```  
  
 Cette commande ajoute un compte d'utilisateur de domaine Windows au premier rôle dans un tableau, où le tableau est créé en répertoriant les enfants du dossier Rôles, dans le contexte d'une base de données spécifique (AWTEST).  
  
## Voir aussi  
 [PowerShell scripting in Analysis Services](../../analysis-services/instances/powershell-scripting-in-analysis-services.md)   
 [Gérer les modèles tabulaires à l'aide de PowerShell](http://go.microsoft.com/fwlink/?linkID=227685)  
  
  