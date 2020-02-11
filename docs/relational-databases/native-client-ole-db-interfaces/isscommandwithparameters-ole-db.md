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
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 08291b998c0f540b56cad59d29433135993487c8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "73761961"
---
# <a name="isscommandwithparameters-ole-db"></a>ISSCommandWithParameters (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  **ISSCommandWithParameters** expose la prise [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en charge de XML et des types définis par l’utilisateur (UDT). Il s'agit d'une interface facultative qui hérite de l'interface OLE DB de base **ICommandWithParameters**. Outre les trois méthodes héritées de **ICommandWithParameters**( **GetParameterInfo**, **MapParameterNames**et **SetParameterInfo**) **ISSCommandWithParameters** fournit deux nouvelles méthodes permettant de gérer des types de données spécifiques au serveur.  
  
> [!NOTE]  
>  L'interface **ISSCommandWithParameters** peut être utilisée lorsque des composants de service sont utilisés, mais ceux-ci n'utilisent pas cette interface.  
  
|Méthode|Description|  
|------------|-----------------|  
|[ISSCommandWithParameters :: GetParameterProperties &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-getparameterproperties-ole-db.md)|Retourne une structure de jeu de propriétés **SSPARAMPROPS** dans le tableau pour chaque paramètre UDT ou XML passé à la commande, mais rien n'est retourné pour d'autres types de paramètres.|  
|[ISSCommandWithParameters :: SetParameterProperties &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-setparameterproperties-ole-db.md)|Définit les propriétés de paramètre pour chaque paramètre par ordinal ou définit des propriétés de paramètre en bloc en spécifiant un tableau de structures **SSPARAMPROPS** .|  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces &#40;OLE DB&#41;](https://msdn.microsoft.com/library/34c33364-8538-45db-ae41-5654481cda93)   
 [Utilisation des types de données XML](../../relational-databases/native-client/features/using-xml-data-types.md)   
 [Utilisation des types définis par l'utilisateur](../../relational-databases/native-client/features/using-user-defined-types.md)  
  
  
