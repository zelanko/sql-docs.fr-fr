---
title: Applet de commande Invoke-ProcessTable | Documents Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 865e6d06-b99a-41f3-9d6f-c3c97b529b23
caps.latest.revision: "9"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 01d14a3ee7db466f184cb99fbb271520ab448244
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2017
---
# <a name="invoke-processtable-cmdlet"></a>Applet de commande Invoke-ProcessTable
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Effectue le **processus** opération sur un **Table** avec un spécifique **RefreshType**.  

>[!NOTE] 
>Cet article peut contenir des exemples et des informations obsolètes. Utilisez l’applet de commande Get-Help pour la dernière version.
  
## <a name="syntax"></a>Syntaxe  
 `Invoke-ProcessTable [-DatabaseName] <string> [-TableName] <string> [-RefreshType] <RefreshType> {Full |     ClearValues | Calculate | DataOnly | Automatic | Add | Defragment} [-Server <string>] [-Credential <pscredential>     [-WhatIf] [-Confirm]  [<CommonParameters>]`  
  
 `Invoke-ProcessTable -RefreshType <RefreshType> {Full | ClearValues | Calculate | DataOnly | Automatic | Add |     Defragment} -Table <Table> [-Server <string>] [-Credential <pscredential>] [-WhatIf] [-Confirm]     [<CommonParameters>]`  
  
## <a name="parameters"></a>Paramètres  
  
### <a name="-tablename-string"></a>-TableName \<chaîne >  
 Nom de la table à laquelle appartient la partition à traiter.  
  
|||  
|-|-|  
|Requis ?|true|  
|Position ?|0|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### <a name="-databasename-string"></a>-DatabaseName \<chaîne >  
 Spécifie la base de données à laquelle appartient la table.  
  
|||  
|-|-|  
|Requis ?|true|  
|Position ?|0|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### <a name="-servermicrosoftanalysissevicesserver"></a>-Server\<Microsoft.AnalysisSevices.Server >  
 Spécifie éventuellement l’instance de serveur à laquelle se connecter si vous n’utilisez pas le répertoire de fournisseur **SQLAS** correspondant au contexte.  
  
|||  
|-|-|  
|Requis ?|false|  
|Position ?|nommée|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### <a name="-refreshtype-microsoftanalysisservicesrefreshtype"></a>-RefreshType \<Microsoft.AnalysisServices.RefreshType >  
 Spécifie le type de processus pour une base de données tabulaire.  Les valeurs valides sont Full, ClearValues, Calculate, DataOnly, Automatic, Add et Defragment. Consultez [Traiter une base de données, une table ou une partition &#40;Analysis Services&#41;](../../analysis-services/tabular-models/process-database-table-or-partition-analysis-services.md) pour des descriptions et des conseils.  
  
|||  
|-|-|  
|Requis ?|true|  
|Position ?|1|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### <a name="-credential"></a>-Credential  
 Si ce paramètre est déclaré, le nom d’utilisateur et le mot de passe transmis seront utilisés pour se connecter à l’instance d’Analysis Services. Si aucune information d’identification n’est indiquée, le compte Windows par défaut de l’utilisateur qui exécute le script est utilisé.  
  
|||  
|-|-|  
|Requis ?|false|  
|Position ?|nommée|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### <a name="-whatif"></a>-Whatif  
 Incluez ce paramètre pour obtenir des informations sur l’impact de l’opération avant son exécution.  
  
|||  
|-|-|  
|Requis ?|false|  
|Position ?|nommée|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### <a name="-confirm"></a>-Confirm  
 Incluez ce paramètre pour confirmer interactivement l’opération par une réponse (oui ou non) avant son exécution.  
  
|||  
|-|-|  
|Requis ?|false|  
|Position ?||  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?||  
|Accepter les caractères génériques ?|false|  
  
## <a name="example-1"></a>Exemple 1  
 `PS SQLSERVER:\SQLAS\MachineName\Instance\Databases\DB1\> Invoke-ProcessTable -TableName "myTable" -Database "DB1"  -RefreshType "Full"`  
  
 Cette commande fournit l’identité de la table à traiter.  
  
## <a name="example-2"></a>Example 2  
 `PS SQLSERVER:\SQLAS\MachineName\Instance\Databases\DB1\> Invoke-ProcessTable -TableName "myTable" -Database "DB1"  -RefreshType [Microsoft.AnalysisServices.Tabular.RefreshType]::Full`  
  
 Cette commande traite une table de métadonnées tabulaires avec un type d’actualisation **enum** .  
  
  
