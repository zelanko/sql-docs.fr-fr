---
title: "Applet de commande New-PowerPivotServiceApplication | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 7bb2a2d2-04c8-43d4-a0fc-e8339ea22138
caps.latest.revision: 10
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 10
---
# Applet de commande New-PowerPivotServiceApplication
  Crée une application de service [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .  
  
 **S'applique à :** SharePoint 2010 et SharePoint 2013.  
  
## Syntaxe  
  
```  
New-PowerPivotServiceApplication [-ServiceApplicationName] <string> [-DatabaseServerName] <string> [-DatabaseName] <string> [-AddToDefaultProxyGroup <switch>] [<CommonParameters>]  
```  
  
## Description  
 L’applet de commande New-PowerPivotServiceApplication permet de créer une application de service [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] dans la batterie de serveurs. Vous devez définir au moins une application de service et celle-ci doit être membre du groupe de service de proxy par défaut. Éventuellement, vous pouvez créer des applications de service supplémentaires si vous devez utiliser plusieurs propriétés ou paramètres de configuration différents. Les applications de service supplémentaires doivent être membres des groupes de connexion de service personnalisés. Une seule application de service [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] peut être membre du groupe de proxys par défaut.  
  
 Une nouvelle application de service est créée à l'aide d'une configuration par défaut. Pour personnaliser les propriétés de configuration, utilisez l'applet de commande Set-PowerPivotServiceApplication.  
  
## Paramètres  
  
### -ServiceApplicationName \<string>  
 Définit le nom d'affichage de l'application de service.  
  
|||  
|-|-|  
|Requis ?|true|  
|Position ?|0|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### -DatabaseServerName \<string>  
 Spécifie une instance du moteur de base de données relationnelle SQL Server qui héberge la base de données d'application. Par défaut, vous pouvez utiliser le serveur de base de données de la batterie de serveurs, ou vous pouvez choisir un autre serveur de base de données pour lequel vous disposez des droits requis pour créer des bases de données.  
  
|||  
|-|-|  
|Requis ?|true|  
|Position ?|1|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### -DatabaseName \<string>  
 Spécifie le nom de la base de données relationnelle SQL Server qui stocke les données d'application. Veillez à spécifier un nom qui correspond à l'application afin que vous puissiez plus facilement identifier sa fonction. Vous pouvez créer une base de données ou spécifier une base de données d’application de service [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] existante pour l’application que vous créez.  
  
|||  
|-|-|  
|Requis ?|true|  
|Position ?|2|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### -AddToDefaultProxyGroup \<switch>  
 Crée une connexion de service [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] dans le groupe de connexions de service par défaut. Les associations entre les applications Web et les applications de service sont déterminées par l'appartenance à ce groupe. Toutes les applications web abonnées au groupe de connexions de service par défaut peuvent utiliser l’application de service [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] que vous ajoutez au groupe. Bien que vous puissiez disposer de plusieurs applications de service [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] dans une batterie de serveurs, une seule application de service peut être membre du groupe de connexions de service par défaut.  
  
 Si vous disposez déjà d’une application de service [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] membre du groupe de proxys par défaut, vous devez définir AddToDefautlProxyGroup:$false pour l’application que vous créez. Vous devez ajouter la nouvelle application de service à un groupe de connexions de service personnalisé.  Vous pouvez utiliser les applets de commande SharePoint intégrées à cet effet.  Get-SPServiceApplicationProxyGroup retourne la liste des groupes de connexions de service définis dans la batterie.  
  
|||  
|-|-|  
|Requis ?|false|  
|Position ?|nommée|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### \<CommonParameters>  
 Cette applet de commande prend en charge les paramètres communs : Verbose, Debug, ErrorAction, ErrorVariable, WarningAction, WarningVariable, OutBuffer et OutVariable. Pour plus d’informations, consultez [About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## Entrées et sorties  
 Le type d'entrée correspond au type des objets que vous pouvez canaliser vers l'applet de commande. Le type de retour correspond au type des objets retournés par l'applet de commande.  
  
|||  
|-|-|  
|Entrées|Aucun.|  
|Sorties|Aucun.|  
  
## Exemple 1  
  
```  
C:\PS>New-PowerPivotServiceApplication -ServiceApplicationName "PowerPivot Service Application" -DatabaseServerName "AdvWorks-SRV01\PowerPivot" -DatabaseName "PowerPivotServiceApp1" -AddtoDefaultProxyGroup:$true  
```  
  
 Cet exemple crée une application de service. La base de données d’application de service est créée sur un serveur de base de données nommé AdvWorks-SRV01 qui a été installé en tant qu’instance nommée [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)], configuration commune à de nombreuses installations [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint. Vous devez disposer d'autorisations dbcreator sur l'instance de SQL Server pour créer la base de données. Vous devez être db_owner sur la base de données de configuration SharePoint. Étant donné qu’il s’agit de la première application de service [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] de la batterie de serveurs, celle-ci doit être membre du groupe de proxys par défaut.  
  
  