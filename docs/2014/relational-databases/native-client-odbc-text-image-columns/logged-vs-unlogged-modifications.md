---
title: Modifications journalisées et non journalisées | Microsoft Docs
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63195137"
---
# <a name="logged-vs-unlogged-modifications"></a>Modifications enregistrées ou non enregistrées
  Une application peut demander que le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client n’enregistre pas les modifications **Text**, **ntext**et **image** . Il convient toutefois d'être prudent lors de l'utilisation de cette option. Elle ne doit être utilisée que dans les cas où les données **Text**, **ntext**ou **image** ne sont pas critiques et que les propriétaires de données sont prêts à échanger la possibilité de récupérer les données pour des performances supérieures.  
  
 La journalisation des modifications de **texte**, **ntext**et **image** est contrôlée en appelant [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) avec le paramètre d' *attribut* défini sur SQL_SOPT_SS_ TEXTPTR_LOGGING et *ValuePtr* défini sur SQL_TL_ON ou SQL_TL_OFF.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des colonnes text et image](managing-text-and-image-columns.md)  
  
  
