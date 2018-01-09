---
title: Applet de commande Get-PowerPivotSystemService | Documents Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 33231250-3880-4d75-936b-d70662a01855
caps.latest.revision: "9"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 20c13c68abadafcbe4cc357345a4b3ba7d0668f7
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="get-powerpivotsystemservice-cmdlet"></a>Applet de commande Get-PowerPivotSystemService
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Retourne les propriétés globales de la [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] objet du Service système dans une batterie de serveurs. 

>[!NOTE] 
>Cet article peut contenir des exemples et des informations obsolètes. Utilisez l’applet de commande Get-Help pour la dernière version.
  
 **S'applique à :** SharePoint 2010 et SharePoint 2013.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Get-PowerPivotSystemService [-Identity <PowerPivotMidTierServicePipeBind>] [<CommonParameters>]  
```  
  
## <a name="description"></a>Description  
 L’applet de commande Get-PowerPivotSystemService retourne les propriétés globales de l’objet de service système [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Il existe un objet parent par batterie de serveurs, mais chaque batterie peut avoir plusieurs instances du service système [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] qui s’exécutent sur des serveurs d’applications distincts de la batterie. L'objet parent affiche les paramètres de niveau batterie qui ne varient pas en fonction de l'instance. Si la batterie comprend plusieurs installations de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint, une liste des instances, séparées par des virgules, indique le nombre d’instances du service système [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] figurant dans la batterie.  
  
## <a name="parameters"></a>Paramètres  
  
### <a name="-identity-powerpivotmidtierservicepipebind"></a>-Identité \<PowerPivotMidTierServicePipeBind >  
 Spécifie l'objet parent à obtenir. La valeur doit être un GUID valide qui identifie l'objet de manière unique dans la batterie.  
  
|||  
|-|-|  
|Requis ?|false|  
|Position ?|0|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|true|  
|Accepter les caractères génériques ?|false|  
  
### <a name="commonparameters"></a>\<Paramètres_courants >  
 Cette applet de commande prend en charge les paramètres communs : Verbose, Debug, ErrorAction, ErrorVariable, WarningAction, WarningVariable, OutBuffer et OutVariable. Pour plus d’informations, consultez [About_Commonparameters](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## <a name="inputs-and-outputs"></a>Entrées et sorties  
 Le type d'entrée correspond au type des objets que vous pouvez canaliser vers l'applet de commande. Le type de retour correspond au type des objets retournés par l'applet de commande.  
  
|||  
|-|-|  
|Entrées|Aucun.|  
|Sorties|Aucun.|  
  
## <a name="example-1"></a>Exemple 1  
  
```  
C:\PS>Get-PowerPivotSystemService  
```  
  
 Cet exemple renvoie les propriétés globales de l’objet parent, en affichant les propriétés qui sont communes à toutes les instances du service système [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] dans la batterie.  
  
  
