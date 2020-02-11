---
title: Conversion des données de paramètre table et autres erreurs et avertissements | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), data conversion
- table-valued parameters (ODBC), error messages
ms.assetid: edd45234-59dc-4338-94fc-330e820cc248
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 576e8e49411412264afc5828fe606a19cc3751f6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62468252"
---
# <a name="table-valued-parameter-data-conversion-and-other-errors-and-warnings"></a>Conversion des données des paramètres table et autres erreurs et avertissements
  Les valeurs de colonne de paramètre table peuvent être converties du type de données client en type de données serveur de la même manière que toute autre valeur de colonne ou de paramètre. Toutefois, dans la mesure où un paramètre table peut contenir plusieurs colonnes et plusieurs lignes, il est important de pouvoir identifier la valeur réelle sur laquelle l'erreur s'est produite.  
  
 Lorsqu'une erreur ou un avertissement est détecté dans une colonne de paramètre table, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client génère un enregistrement de diagnostic. Le message d'erreur contient le numéro du paramètre table, accompagné de l'ordinal de colonne et du numéro de ligne. Une application peut également utiliser les champs de diagnostic SQL_DIAG_SS_TABLE_COLUMN_NUMBER et SQL_DIAG_SS_TABLE_ROW_NUMBER dans des enregistrements de diagnostic pour déterminer quelles valeurs sont associées à des erreurs et des avertissements. Ces champs de diagnostic sont disponibles dans [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et versions ultérieures.  
  
 Les composants SQLSTATE et message des enregistrements de diagnostic sont conformes au comportement ODBC existant pour tous les autres aspects. Autrement dit, à l’exception des informations d’identification des paramètres, des lignes et des colonnes, les messages d’erreur ont les mêmes valeurs pour les paramètres table que pour les paramètres qui ne sont pas des tables.  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres table &#40;ODBC&#41;](table-valued-parameters-odbc.md)  
  
  
