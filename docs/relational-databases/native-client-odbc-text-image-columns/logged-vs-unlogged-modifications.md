---
title: Modifications Enregistrées ou non les Modifications | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-odbc-text-image-columns
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- text columns [ODBC]
- SQL Server Native Client ODBC driver, image columns
- SQL Server Native Client ODBC driver, text columns
- data types [ODBC], image
- data types [ODBC], text
- logged vs. nonlogged modifications [SQL Server Native Client]
- columns [ODBC]
- ODBC data types, image columns
- nonlogged vs. logged modifications
- ODBC data types, text columns
- image columns [ODBC]
ms.assetid: 20aa5b27-4a2c-46e7-8356-beb0eebf4b7e
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: b84160c6f054c5ff24230df3bb84a213f2d31919
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39536759"
---
# <a name="logged-vs-unlogged-modifications"></a>Modifications enregistrées ou non enregistrées
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Une application peut demander que le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le pilote ODBC Native Client pas journal **texte**, **ntext**, et **image** modifications. Il convient toutefois d'être prudent lors de l'utilisation de cette option. Il doit être utilisé uniquement dans les cas où le **texte**, **ntext**, ou **image** données ne sont pas critiques et les propriétaires de données sont prêts à compenser la possibilité de récupérer des données pour performances plus élevées.  
  
 La journalisation de **texte**, **ntext**, et **image** modifications est contrôlé par l’appel [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) avec la  *Attribut* paramètre défini à SQL_SOPT_SS_ TEXTPTR_LOGGING et *ValuePtr* défini à SQL_TL_ON ou SQL_TL_OFF.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des colonnes texte et image](../../relational-databases/native-client-odbc-text-image-columns/managing-text-and-image-columns.md)  
  
  
