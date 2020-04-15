---
title: Tampons différés (en anglais) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- buffers [ODBC], deferred
- deferred buffers [ODBC]
ms.assetid: 02c9a75c-2103-4f68-a1db-e31f7e0f1f03
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f34c6d3d886a0a75c309dc4f5c71f5c7ba3df447
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305980"
---
# <a name="deferred-buffers"></a>Mémoires tampons différées
Un *tampon différé* est celui dont la valeur est utilisée à un moment *donné après* qu’il soit spécifié dans un appel de fonction. Par exemple, **SQLBindParameter** est utilisé pour associer ou *lier* un tampon de données avec un paramètre dans une déclaration SQL. L’application précise le nombre du paramètre et passe l’adresse, la longueur des bytes et le type de tampon. Le conducteur enregistre ces informations mais n’examine pas le contenu du tampon. Plus tard, lorsque l’application exécute l’instruction, le pilote récupère les informations et les utilise pour récupérer les données de paramètres et les envoyer à la source de données. Par conséquent, l’entrée des données dans le tampon est reportée. Étant donné que les tampons différés sont spécifiés dans une fonction et utilisés dans une autre, il s’agit d’une erreur de programmation d’application pour libérer un tampon différé pendant que le conducteur s’attend toujours à ce qu’il existe; pour plus d’informations, voir [Allocating and Freeing Buffers](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md), plus tard dans cette section.  
  
 Les tampons d’entrée et de sortie peuvent être reportés. Le tableau suivant résume les utilisations de tampons différés. Notez que les tampons différés liés aux colonnes définies de résultat sont spécifiés avec **SQLBindCol**, et que les tampons différés liés aux paramètres de l’énoncé SQLL sont spécifiés avec **SQLBindParameter**.  
  
|Utilisation de tampon|Type|Spécifié avec|Utilisée par|  
|----------------|----------|--------------------|-------------|  
|Envoi de données pour les paramètres d’entrée|Entrée différée|**SQLBindParameter**|**SQLExecute**<br /> **SQLExecDirect**|  
|Envoi de données pour mettre à jour ou insérer une ligne dans un ensemble de résultats|Entrée différée|**SQLBindCol**|**SQLSetPos**|  
|Retour des données pour les paramètres de sortie et d’entrée/sortie|Sortie différée|**SQLBindParameter**|**SQLExecute**<br /> **SQLExecDirect**|  
|Données de l’ensemble des résultats de retour|Sortie différée|**SQLBindCol**|**SQLFetch**<br /> **SQLFetchScroll SQLSetPos**|
