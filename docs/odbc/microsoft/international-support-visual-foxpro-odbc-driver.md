---
title: Prise en charge internationale (pilote ODBC de Visual FoxPro) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- double-byte character sets [ODBC]
- FoxPro ODBC driver [ODBC], international support
- DBCS [ODBC]
- international support [ODBC]
- sort order [ODBC]
- collating sequences [ODBC]
- Visual FoxPro ODBC driver [ODBC], international support
ms.assetid: cd3fab32-13f1-4a86-abc4-5e18667669fc
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 50d65520e74a4e11bada88795fedc0b2f2e82628
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47853097"
---
# <a name="international-support-visual-foxpro-odbc-driver"></a>Prise en charge internationale (pilote ODBC Visual FoxPro)
Le pilote ODBC Visual FoxPro Microsoft prend en charge :  
  
-   Les caractères codés sur deux définit (DBCS)  
  
-   Plusieurs séquences de classement  
  
 Définit un ordre de tri le *ordre de tri* pour les données stockées dans une table Visual FoxPro ou d’une base de données. Par défaut, le pilote est configuré pour utiliser des séquences de classement qui prennent en charge la version de langue de votre système d’exploitation.  
  
 Pour obtenir la liste de séquences de classement pris en charge, consultez [définir COLLATE](../../odbc/microsoft/set-collate-command.md).  
  
## <a name="locale"></a>paramètres régionaux  
 L’ensemble d’informations qui correspondant à un langage donné et un pays/région. Paramètres régionaux indique des paramètres spécifiques tels que les séparateurs décimaux, de date et de formats d’heure et d’ordre de tri des caractères.  
  
## <a name="sort-order"></a>ordre de tri  
 Ordres de tri incorporent les règles de tri de différentes *paramètres régionaux*s, ce qui vous permet de trier correctement les données dans ces langues. Dans Visual FoxPro, l’ordre de tri actuelle détermine les résultats des comparaisons d’expression de caractères et l’ordre dans lequel les enregistrements apparaissent dans indexé ou triées de tables.
