---
title: Ensemble de lignes DISCOVER_DATASOURCES | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- DISCOVER_DATASOURCES
topic_type:
- apiref
helpviewer_keywords:
- DISCOVER_DATASOURCES rowset
ms.assetid: f3ff26ab-a447-416b-ba54-1716df2283de
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 32e7aa7327cce301cc8415f45635fda651d861f2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36040069"
---
# <a name="discoverdatasources-rowset"></a>Ensemble de lignes DISCOVER_DATASOURCES
  Retourne la liste des sources de données du fournisseur XML for Analysis (XMLA) qui sont disponibles sur le serveur ou le service Web. Les sources de données publiées sont retournées à partir d'une URL du serveur Web d'application. Le client peut se connecter à l'une des sources de données indiquées dans cette liste.  
  
 Si vous appelez le [Discover](../../xmla/xml-elements-methods-discover.md) méthode avec la `DISCOVER_DATASOURCES` valeur d’énumération dans le [RequestType](../../xmla/xml-elements-properties/type-element-xmla.md) élément, le `Discover` méthode retourne la `DISCOVER_DATASOURCES` ensemble de lignes.  
  
 **S'applique à :** modèles tabulaires, modèles multidimensionnels  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 Le client sélectionne une source de données en définissant le `DataSourceInfo` propriété dans le [propriétés](../../xmla/xml-elements-properties/properties-element-xmla.md) élément qui est envoyé avec la [commande](../../xmla/xml-elements-properties/command-element-xmla.md) élément par le [Execute](../../xmla/xml-elements-methods-execute.md) méthode. Un client ne doit pas construire le contenu de la propriété `DataSourceInfo` à envoyer au serveur. À la place, le client doit utiliser la méthode `Discover` pour rechercher les sources de données que le fournisseur prend en charge. Le client renvoie ensuite pour la propriété `DataSourceInfo` la valeur qu'il obtient de l'ensemble de lignes `DISCOVER_DATASOURCES`.  
  
 Le `DISCOVER_DATASOURCES` ensemble de lignes contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Restriction|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|`DataSourceName`|`DBTYPE_WSTR`|Oui|Nom de la source de données, par exemple `Adventure Works`.|  
|`DataSourceDescription`|`DBTYPE_WSTR`||Description de la source de données entrée par le serveur de publication.<br /><br /> Peut retourner `NULL`.|  
|`URL`|`DBTYPE_WSTR`|Oui|Chemin d'accès unique qui indique où appeler les méthodes XML for Analysis (XMLA) pour cette source de données.<br /><br /> Peut retourner `NULL`.|  
|`DataSourceInfo`|`DBTYPE_WSTR`||Chaîne qui contient les informations supplémentaires requises pour établir la connexion à la source de données.<br /><br /> Peut retourner `NULL`.|  
|`ProviderName`|`DBTYPE_WSTR`|Oui|Nom du fournisseur de la source de données.<br /><br /> Exemple : `"MSOLAP"`<br /><br /> Peut retourner `NULL`.|  
|`ProviderType`|`DBTYPE_WSTR`|Oui|Types de données pris en charge par le fournisseur. Ce tableau peut inclure un ou plusieurs des types suivants :<br /><br /> `MDP` : fournisseur de données multidimensionnelles.<br /><br /> `TDP`: fournisseur de données sous forme de tableau.<br /><br /> `DMP` : fournisseur d'exploration de données (implémente la spécification OLE DB pour l'exploration de données).|  
|`AuthenticationMode`|`DBTYPE_WSTR`|Oui|Spécification du type de mode de sécurité que la source de données utilise. Il peut s'agir de l'une des valeurs suivantes :<br /><br /> `Unauthenticated` : aucun ID d'utilisateur ou mot de passe ne doit être envoyé.<br /><br /> `Authenticated` : l'ID d'utilisateur et le mot de passe doivent être inclus dans les informations requises pour établir la connexion à la source de données.<br /><br /> `Integrated` : la source de données utilise la sécurité sous-jacente pour déterminer l'autorisation, telle que la sécurité intégrée fournie par [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Internet Information Services (IIS).|  
  
 Cet ensemble de lignes de schéma n'est pas trié.  
  
> [!IMPORTANT]  
>  L'ensemble de lignes `DISCOVER_DATASOURCES` ne peut pas être interrogé à l'aide de requêtes DMV et de la syntaxe de la commande SELECT. Toutefois, l'ensemble de lignes `DISCOVER_DATASOURCES` peut être interrogé à l'aide de la méthode <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.GetSchemaDataSet%2A>  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Utilisation d'ADOMD.NET pour retourner l'ensemble de lignes  
 Lorsque vous utilisez ADOMD.NET et l'ensemble de lignes de schéma pour récupérer des métadonnées, vous pouvez utiliser un GUID ou une chaîne pour référencer un objet d'ensemble de lignes de schéma dans la méthode GetSchemaDataSet. Pour plus d'informations, consultez [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md).  
  
 Le tableau suivant fournit le GUID et les valeurs de chaîne qui identifient cet ensemble de lignes.  
  
|Argument|Valeur|  
|--------------|-----------|  
|GUID|06c03d41-f66d-49f3-b1b8-987f7af4cf18|  
|ADOMDNAME|DataSources|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma XML for Analysis](xml-for-analysis-schema-rowsets.md)  
  
  