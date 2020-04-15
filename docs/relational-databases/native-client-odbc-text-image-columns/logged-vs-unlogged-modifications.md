---
title: Modifications enregistrées par rapport à l’enroulement Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: dc7fb913bef4083b045a0c1c010bdedbc43135c5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297652"
---
# <a name="logged-vs-unlogged-modifications"></a>Modifications enregistrées ou non enregistrées
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Une application peut [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] demander au conducteur native d’ODBC de ne pas enregistrer **de texte,** **de ntext**et de modifications **d’image.** Il convient toutefois d'être prudent lors de l'utilisation de cette option. Il ne doit être utilisé que pour les situations où le **texte,** **le ntext**, ou les données **d’image** n’est pas critique et les propriétaires de données sont prêts à échanger la capacité de récupérer des données pour des performances plus élevées.  
  
 L’enregistrement du **texte,** **du ntext**, et des modifications **d’image** est contrôlé en appelant [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) avec le paramètre *d’attribut* réglé pour SQL_SOPT_SS_ TEXTPTR_LOGGING et *ValuePtr* réglé à SQL_TL_ON ou SQL_TL_OFF.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des colonnes texte et image](../../relational-databases/native-client-odbc-text-image-columns/managing-text-and-image-columns.md)  
  
  
