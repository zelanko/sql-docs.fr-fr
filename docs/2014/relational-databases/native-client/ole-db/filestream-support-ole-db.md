---
title: Prise en charge FILESTREAM (OLE DB) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB [FILESTREAM support]
- FILESTREAM [SQL Server], OLE DB
ms.assetid: c2bd3dfd-6103-43d1-859e-8ed8d19c58d3
caps.latest.revision: 13
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ba270b26a5a290f5b5c6fdd2830f10b9bf695037
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36041347"
---
# <a name="filestream-support-ole-db"></a>Prise en charge de FILESTREAM (OLE DB)
  À partir de [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] et [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0, OLE DB prend en charge la fonctionnalité FILESTREAM améliorée. Pour plus d’informations sur cette fonctionnalité, consultez [prise en charge FILESTREAM](../features/filestream-support.md). Pour obtenir des exemples, consultez [Filestream et OLE DB](../../native-client-ole-db-how-to/filestream/filestream-and-ole-db.md).  
  
 Pour envoyer et recevoir des valeurs `varbinary(max)` supérieures à 2 Go, une application utilise `DBTYPE_IUNKNOWN` dans les liaisons de résultat et de paramètre. Pour les paramètres du fournisseur doit appeler IUnknown::QueryInterface pour ISequentialStream et pour les résultats qui retournent ISequentialStream.  
  
 Pour OLE DB, la vérification associées aux valeurs de ISequentialStream sera levée. Lorsque *wType* est `DBTYPE_IUNKNOWN` dans les `DBBINDING` struct, la vérification de la longueur peut être désactivée en omettant `DBPART_LENGTH` de *dwPart* ou en définissant la longueur des données (à l’offset *obLength* dans le tampon de données) à ~ 0. Dans ce cas, le fournisseur ne vérifiera pas la longueur de la valeur et demandera et retournera toutes les données disponibles par le biais du flux de données. Cette modification sera appliquée à tous les types d'objets volumineux (LOB) et XML, mais uniquement en cas de connexion à des serveurs [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] (ou ultérieurs). Cela offrira une plus grande souplesse aux développeurs, tout en maintenant la cohérence et la compatibilité descendante des applications existantes et des serveurs de niveau inférieur.  
  
 Cette modification affecte toutes les interfaces qui transfèrent des données, principalement IRowset::GetData ICommand::Execute et IRowsetFastLoad::InsertRow.  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation de SQL Server Native Client](../sql-server-native-client-programming.md)  
  
  