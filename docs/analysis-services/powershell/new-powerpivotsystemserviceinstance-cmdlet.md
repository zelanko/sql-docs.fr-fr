---
title: Applet de commande New-PowerPivotSystemServiceInstance | Documents Microsoft
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
ms.assetid: 7ea94113-c0f1-4cca-9228-f1a034fba5db
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f2e412047e4d859de637da933d2335232961ee13
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2018
---
# <a name="new-powerpivotsystemserviceinstance-cmdlet"></a>Applet de commande New-PowerPivotSystemServiceInstance
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Ajoute une nouvelle instance de service système [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] à un serveur d’applications.  

>[!NOTE] 
>Cet article peut contenir des exemples et des informations obsolètes. Utilisez l’applet de commande Get-Help pour la dernière version.
  
 **S'applique à :** SharePoint 2010 et SharePoint 2013.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
New-PowerPivotSystemServiceInstance [[-ParentService] <PowerPivotMidTierServicePipeBind>] [-SystemServiceInstanceName <string>] [-Provision] [<CommonParameters>]  
```  
  
## <a name="description"></a> Description  
 L’applet de commande New-PowerPivotSystemServiceInstance configure un nouvel objet PowerPivotSystemService au niveau de la batterie une fois que vous avez utilisé le programme d’installation de SQL Server pour installer [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint sur le serveur d’applications local. Vous ne pouvez configurer qu'une seule instance du service sur chaque serveur d'applications.  Si le service est déjà configuré, vous ne pouvez pas exécuter cette applet de commande.  
  
## <a name="parameters"></a>Paramètres  
  
### <a name="-parentservice-powerpivotmidtierservicepipebind"></a>-ParentService \<PowerPivotMidTierServicePipeBind>  
 Spécifie le GUID de l’objet parent du service système [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] dans la batterie. Dans cette version, un seul objet parent est autorisé. Vous pouvez utiliser l'applet de commande Get-PowerPivotSystemService pour retourner l'objet de service ou son GUID.  
  
|||  
|-|-|  
|Requis ?|false|  
|Position ?|0|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|true|  
|Accepter les caractères génériques ?|false|  
  
### <a name="-systemserviceinstancename-string"></a>-SystemServiceInstanceName \<string>  
 Spécifie un nom qui identifie cet objet.  
  
|||  
|-|-|  
|Requis ?|false|  
|Position ?|1|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### <a name="provision-switchparameter"></a>Configurer [\<Paramètre_booléen >]  
 Rend le service accessible sur SharePoint. Les valeurs valides sont $true ou $false.  
  
|||  
|-|-|  
|Requis ?|false|  
|Position ?|nommée|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### <a name="commonparameters"></a>\<CommonParameters>  
 Cette applet de commande prend en charge les paramètres communs : Verbose, Debug, ErrorAction, ErrorVariable, WarningAction, WarningVariable, OutBuffer et OutVariable. Pour plus d’informations, consultez [About_Commonparameters](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## <a name="inputs-and-outputs"></a>Entrées et sorties  
 Le type d'entrée correspond au type des objets que vous pouvez canaliser vers l'applet de commande. Le type de retour correspond au type des objets retournés par l'applet de commande.  
  
|||  
|-|-|  
|Entrées|Aucun.|  
|Sorties|Aucun.|  
  
## <a name="example-1"></a>Exemple 1  
  
```  
C:\PS>New-PowerPivotSystemServiceInstance -Provision:$true  
```  
  
 Cet exemple montre la forme la plus commune de l'applet de commande. Il inscrit le service système [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] sur le serveur d’applications local avec la batterie.  
  
## <a name="example-2"></a>Exemple 2  
  
```  
C:\PS>New-PowerPivotSystemServiceInstance -SystemServiceInstanceName "MyPSSInstance" -provision:$false  
```  
  
 Cet exemple nomme l’instance du service système [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , mais sans la configurer. Si vous ne fournissez pas de nom, le nom par défaut, instance de service système SQL Server Analysis Services, est utilisé à la place. La création d'un nom personnalisé pour le service est facultative. Vous pouvez nommer le service pour prendre en charge les scénarios de test, ou si vous disposez d'un outil ou d'un script personnalisé qui configure l'instance à une étape ultérieure.  
  
  
