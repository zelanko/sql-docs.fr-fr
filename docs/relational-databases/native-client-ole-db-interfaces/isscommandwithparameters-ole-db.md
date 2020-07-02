---
title: ISSCommandWithParameters (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- ISSCommandWithParameters (OLE DB)
apitype: COM
helpviewer_keywords:
- ISSCommandWithParameters interface
ms.assetid: 3419b7f3-36a3-4863-816e-e641e4e90496
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f3baeaae6723d3d02e34048e9d223153ed447538
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85785304"
---
# <a name="isscommandwithparameters-ole-db"></a>ISSCommandWithParameters (OLE DB)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  **ISSCommandWithParameters** expose la prise en charge de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML et des types définis par l'utilisateur (UDT). Il s'agit d'une interface facultative qui hérite de l'interface OLE DB de base **ICommandWithParameters**. Outre les trois méthodes héritées de **ICommandWithParameters**( **GetParameterInfo**, **MapParameterNames**et **SetParameterInfo**) **ISSCommandWithParameters** fournit deux nouvelles méthodes permettant de gérer des types de données spécifiques au serveur.  
  
> [!NOTE]  
>   L'interface **ISSCommandWithParameters** peut être utilisée lorsque des composants de service sont utilisés, mais ceux-ci n'utilisent pas cette interface.  
  
|Méthode|Description|  
|------------|-----------------|  
|[ISSCommandWithParameters::GetParameterProperties &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-getparameterproperties-ole-db.md)|Retourne une structure de jeu de propriétés **SSPARAMPROPS** dans le tableau pour chaque paramètre UDT ou XML passé à la commande, mais rien n'est retourné pour d'autres types de paramètres.|  
|[ISSCommandWithParameters::SetParameterProperties &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-setparameterproperties-ole-db.md)|Définit les propriétés de paramètre pour chaque paramètre par ordinal ou définit des propriétés de paramètre en bloc en spécifiant un tableau de structures **SSPARAMPROPS** .|  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces &#40;OLE DB&#41;](https://msdn.microsoft.com/library/34c33364-8538-45db-ae41-5654481cda93)   
 [Utilisation des types de données XML](../../relational-databases/native-client/features/using-xml-data-types.md)   
 [Utilisation des types définis par l'utilisateur](../../relational-databases/native-client/features/using-user-defined-types.md)  
  
  
