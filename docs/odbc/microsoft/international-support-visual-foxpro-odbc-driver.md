---
title: Soutien international (Visual FoxPro ODBC Driver) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b4b0c758bb478ea6a468e6756c3d6f0f52c766f5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299969"
---
# <a name="international-support-visual-foxpro-odbc-driver"></a>Prise en charge internationale (pilote ODBC Visual FoxPro)
Le pilote Microsoft Visual FoxPro ODBC prend en charge :  
  
-   Ensembles de caractères double-byte (DBCS)  
  
-   Séquences de collation multiples  
  
 Une séquence de collecte définit le *tri des* données stockées dans une table ou une base de données Visual FoxPro. Par défaut, le pilote est configuré pour utiliser les séquences de collating qui prennent en charge la version linguistique de votre système d’exploitation.  
  
 Pour une liste de séquences de collation prises en charge, voir [SET COLLATE](../../odbc/microsoft/set-collate-command.md).  
  
## <a name="locale"></a>locale  
 L’ensemble d’informations qui correspond à une langue donnée et un pays/région. Un lieu indique des paramètres spécifiques tels que les séparateurs décimaux, les formats de date et d’heure, et l’ordre de tri des personnages.  
  
## <a name="sort-order"></a>ordre de tri  
 Les ordres de tri intègrent les règles de tri de différents *local*s, vous permettant de trier correctement les données dans ces langues. Dans Visual FoxPro, l’ordre de tri actuel détermine les résultats des comparaisons d’expression des personnages et l’ordre dans lequel les enregistrements apparaissent dans des tableaux indexés ou triés.
