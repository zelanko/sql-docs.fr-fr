---
title: Prise en charge de FILESTREAM (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB [FILESTREAM support]
- FILESTREAM [SQL Server], OLE DB
ms.assetid: c2bd3dfd-6103-43d1-859e-8ed8d19c58d3
author: rothja
ms.author: jroth
ms.openlocfilehash: cde3c2cd1b72773cfcf17eacedeb3276dd2f63da
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85011059"
---
# <a name="filestream-support-ole-db"></a>Prise en charge de FILESTREAM (OLE DB)
  Depuis [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] et [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10,0, OLE DB prend en charge la fonctionnalité FileStream améliorée. Pour plus d’informations sur cette fonctionnalité, consultez [prise en charge de FileStream](../features/filestream-support.md). Pour obtenir des exemples, consultez [Filestream et OLE DB](../../native-client-ole-db-how-to/filestream/filestream-and-ole-db.md).  
  
 Pour envoyer et recevoir des valeurs `varbinary(max)` supérieures à 2 Go, une application utilise `DBTYPE_IUNKNOWN` dans les liaisons de résultat et de paramètre. Pour les paramètres, le fournisseur doit appeler IUnknown::QueryInterface pour ISequentialStream et pour les résultats qui retournent ISequentialStream.  
  
 Pour OLE DB, la vérification en rapport avec les valeurs ISequentialStream sera levée. Quand *wType* se trouve `DBTYPE_IUNKNOWN` dans le `DBBINDING` struct, la vérification de la longueur peut être désactivée en omettant `DBPART_LENGTH` de *dwPart* ou en définissant la longueur des données (au niveau du décalage *obLength* dans le tampon de données) sur ~ 0. Dans ce cas, le fournisseur ne vérifiera pas la longueur de la valeur et demandera et retournera toutes les données disponibles par le biais du flux de données. Cette modification sera appliquée à tous les types d'objets volumineux (LOB) et XML, mais uniquement en cas de connexion à des serveurs [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] (ou ultérieurs). Cela offrira une plus grande souplesse aux développeurs, tout en maintenant la cohérence et la compatibilité descendante des applications existantes et des serveurs de niveau inférieur.  
  
 Cette modification affecte toutes les interfaces qui transfèrent des données, principalement IRowset::GetData, ICommand::Execute et IRowsetFastLoad::InsertRow.  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation de SQL Server Native Client](../sql-server-native-client-programming.md)  
  
  
