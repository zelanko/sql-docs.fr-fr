---
title: "Applet de commande Get-PowerPivotSystemService | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 33231250-3880-4d75-936b-d70662a01855
caps.latest.revision: 9
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 9
---
# Applet de commande Get-PowerPivotSystemService
  Renvoie les propriétés globales de l’objet de service système [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] dans une batterie.  
  
 **S'applique à :** SharePoint 2010 et SharePoint 2013.  
  
## Syntaxe  
  
```  
Get-PowerPivotSystemService [-Identity <PowerPivotMidTierServicePipeBind>] [<CommonParameters>]  
```  
  
## Description  
 L’applet de commande Get-PowerPivotSystemService retourne les propriétés globales de l’objet de service système [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]. Il existe un objet parent par batterie de serveurs, mais chaque batterie peut avoir plusieurs instances du service système [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] qui s’exécutent sur des serveurs d’applications distincts de la batterie. L'objet parent affiche les paramètres de niveau batterie qui ne varient pas en fonction de l'instance. Si la batterie comprend plusieurs installations de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint, une liste des instances, séparées par des virgules, indique le nombre d’instances du service système [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] figurant dans la batterie.  
  
## Paramètres  
  
### -Identity \<PowerPivotMidTierServicePipeBind>  
 Spécifie l'objet parent à obtenir. La valeur doit être un GUID valide qui identifie l'objet de manière unique dans la batterie.  
  
|||  
|-|-|  
|Requis ?|false|  
|Position ?|0|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|true|  
|Accepter les caractères génériques ?|false|  
  
### \<CommonParameters>  
 Cette applet de commande prend en charge les paramètres communs : Verbose, Debug, ErrorAction, ErrorVariable, WarningAction, WarningVariable, OutBuffer et OutVariable. Pour plus d’informations, consultez [About_Commonparameters](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## Entrées et sorties  
 Le type d'entrée correspond au type des objets que vous pouvez canaliser vers l'applet de commande. Le type de retour correspond au type des objets retournés par l'applet de commande.  
  
|||  
|-|-|  
|Entrées|Aucun.|  
|Sorties|Aucun.|  
  
## Exemple 1  
  
```  
C:\PS>Get-PowerPivotSystemService  
```  
  
 Cet exemple renvoie les propriétés globales de l’objet parent, en affichant les propriétés qui sont communes à toutes les instances du service système [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] dans la batterie.  
  
  