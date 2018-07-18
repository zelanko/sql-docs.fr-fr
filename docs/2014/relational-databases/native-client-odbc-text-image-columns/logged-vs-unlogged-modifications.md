---
title: Visual Studio connecté. Enregistrées ou non les Modifications | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
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
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 34064aaa2e96a7d610f8709c1f5750bddd62b766
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37420288"
---
# <a name="logged-vs-unlogged-modifications"></a>Visual Studio connecté. Modifications non enregistrées
  Une application peut demander que le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le pilote ODBC Native Client pas journal **texte**, **ntext**, et **image** modifications. Il convient toutefois d'être prudent lors de l'utilisation de cette option. Il doit être utilisé uniquement dans les cas où le **texte**, **ntext**, ou **image** données ne sont pas critiques et les propriétaires de données sont prêts à compenser la possibilité de récupérer des données pour performances plus élevées.  
  
 La journalisation de **texte**, **ntext**, et **image** modifications est contrôlé par l’appel [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) avec la  *Attribut* paramètre défini à SQL_SOPT_SS_ TEXTPTR_LOGGING et *ValuePtr* défini à SQL_TL_ON ou SQL_TL_OFF.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des colonnes texte et image](managing-text-and-image-columns.md)  
  
  
