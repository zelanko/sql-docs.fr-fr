---
title: ISSCommandWithParameters::SetParameterProperties (OLE DB) | Microsoft Docs
description: ISSCommandWithParameters::SetParameterProperties (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-interfaces
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISSCommandWithParameters::SetParameterProperties (OLE DB)
apitype: COM
helpviewer_keywords:
- SetParameterProperties method
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: e04c6a678e204b741f4e0a494000b04ae575035f
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2018
ms.locfileid: "39106065"
---
# <a name="isscommandwithparameterssetparameterproperties-ole-db"></a>ISSCommandWithParameters::SetParameterProperties (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Définit les propriétés de paramètre pour chaque paramètre par ordinal ou définit des propriétés de paramètre en bloc en spécifiant un tableau de structures SSPARAMPROPS.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
HRESULT SetParameterProperties(  
      DB_UPARAMS cParams,   
      SSPARAMPROPS rgParamProperties[]);  
```  
  
## <a name="arguments"></a>Arguments  
 *cParams*[in]  
 Nombre de structures SSPARAMPROPS dans le tableau *rgParamProperties*. Si ce nombre est égal à zéro, **ISSCommandWithParameters::SetParameterProperties** supprime toutes les propriétés qui ont pu être spécifiées pour les paramètres dans la commande.  
  
 *rgParamProperties*[in]  
 Tableau de structures SSPARAMPROPS à définir.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 La méthode **ISSCommandWithParameters::SetParameterProperties** retourne les mêmes codes d’erreur que la méthode OLE DB **ICommandProperties::SetProperties** principale.  
  
## <a name="remarks"></a>Notes   
 La définition des propriétés de paramètre avec cette méthode est autorisée pour chaque paramètre par ordinal, ou avec un appel unique à **ISSCommandWithParameters::SetParameterProperties**, une fois SSPARAMPROPS créé à partir du tableau de propriétés.  
  
 Vous devez appeler la méthode **SetParameterInfo** avant d’appeler la méthode **ISSCommandWithParameters::SetParameterProperties**. Le fait d'appeler `SetParameterProperties(0, NULL)` efface toutes les propriétés de paramètre spécifiées, tandis que l'appel de `SetParameterInfo(0,NULL,NULL)` efface toutes les informations sur les paramètres y compris toutes les propriétés qui peuvent être associées à un paramètre.  
  
 L’appel de **ISSCommandWithParameters::SetParameterProperties** pour spécifier des propriétés pour un paramètre qui n’est pas du type DBTYPE_XML ou DBTYPE_UDT retourne DB_E_ERRORSOCCURRED ou DB_S_ERRORSOCCURRED et marque le champ *dwStatus* de tous les DBPROP contenus dans SSPARAMPROPS pour ce paramètre avec DBPROPSTATUS_NOTSET. Le tableau DBPROP de chaque DBPROPSET contenu dans SSPARAMPROPS doit être parcouru pour détecter le paramètre auquel DB_E_ERRORSOCCURRED ou DB_S_ERRORSOCCURRED fait référence.  
  
 Si **ISSCommandWithParameters::SetParameterProperties** est appelé pour spécifier les propriétés de paramètres dont les informations sur les paramètres n’ont pas encore été définies avec **SetParameterInfo**, le fournisseur retourne E_UNEXPECTED avec le message d’erreur suivant :  
  
 La méthode SetParameterProperties ne peut pas être appelée pour les paramètres spécifiés sans appeler auparavant la méthode SetParameterInfo. Vous devez définir les informations de paramètre avant de définir les propriétés de paramètre.  
  
 Si l’appel à **ISSCommandWithParameters::SetParameterProperties** contient des paramètres où les informations sur les paramètres ont été définies et quelques paramètres où les informations sur les paramètres n’ont pas été définies, les propriétés dwStatus dans le DBPROPSET du jeu de propriétés SSPARAMPROPS seront retournées avec DBSTATUS_NOTSET.  
  
 La structure SSPARAMPROPS est défini comme suit :  
  
 `struct SSPARAMPROPS {`  
  
 `DBORDINAL iOrdinal;`  
  
 `ULONG cPropertySets;`  
  
 `DBPROPSET *rgPropertySets;`  
  
 `};`  
  
 Améliorations du moteur de base de données en commençant par [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] autoriser ISSCommandWithParameters::SetParameterProperties obtenir des descriptions plus exactes des résultats attendus. Ces résultats plus exacts peuvent différer des valeurs retournées par ISSCommandWithParameters::SetParameterProperties dans les versions précédentes de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Pour plus d’informations, consultez [Découverte des métadonnées](../../oledb/features/metadata-discovery.md).  
  
|Membre|Description|  
|------------|-----------------|  
|*iOrdinal*|Position ordinale du paramètre transmis.|  
|*cPropertySets*|Nombre de structures DBPROPSET dans *rgPropertySets*.|  
|*rgPropertySets*|Pointeur vers la mémoire dans lequel retourner un tableau de structures DBPROPSET.|  
  
## <a name="see-also"></a> Voir aussi  
 [ISSCommandWithParameters &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/isscommandwithparameters-ole-db.md)  
  
  
