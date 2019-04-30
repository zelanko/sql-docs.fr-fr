---
title: Modifications Enregistrées ou non les Modifications | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c722d5360ad01e7e95508c2219ceb674de381286
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63195137"
---
# <a name="logged-vs-unlogged-modifications"></a>Modifications enregistrées ou non enregistrées
  Une application peut demander que le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le pilote ODBC Native Client pas journal **texte**, **ntext**, et **image** modifications. Il convient toutefois d'être prudent lors de l'utilisation de cette option. Il doit être utilisé uniquement dans les cas où le **texte**, **ntext**, ou **image** données ne sont pas critiques et les propriétaires de données sont prêts à compenser la possibilité de récupérer des données pour performances plus élevées.  
  
 La journalisation de **texte**, **ntext**, et **image** modifications est contrôlé par l’appel [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) avec la  *Attribut* paramètre défini à SQL_SOPT_SS_ TEXTPTR_LOGGING et *ValuePtr* défini à SQL_TL_ON ou SQL_TL_OFF.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des colonnes texte et image](managing-text-and-image-columns.md)  
  
  
