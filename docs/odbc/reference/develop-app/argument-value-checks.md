---
title: Vérifications de la valeur de l’argumentation (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], driver manager error checking
- argument value checks [ODBC]
- driver manager [ODBC], error checking
ms.assetid: 37a65f8b-83aa-456c-b7cf-500404abb38a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6c6e4de16c4a1a80be893acbc7a1993b375f2fee
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298820"
---
# <a name="argument-value-checks"></a>Vérifications de la valeur des arguments
Le gestionnaire de conducteur vérifie les types d’arguments suivants. Sauf indication contraire, le gestionnaire de conducteur renvoie SQL_ERROR pour des erreurs dans les valeurs d’argumentation.  
  
-   L’environnement, la connexion et les poignées de déclaration ne peuvent généralement pas être des pointeurs nuls. Le gestionnaire de conducteur retourne SQL_INVALID_HANDLE lorsqu’il trouve une poignée nulle.  
  
-   Les arguments de pointeurs requis, tels que *OutputHandlePtr* dans **SQLAllocHandle** et *CursorName* dans **SQLSetCursorName**, ne peuvent pas être des pointeurs nuls.  
  
-   Les indicateurs d’option qui ne prennent pas en charge les valeurs spécifiques au conducteur doivent être une valeur juridique. Par exemple, *l’opération* dans **SQLSetPos** doit être SQL_POSITION, SQL_REFRESH, SQL_UPDATE, SQL_DELETE ou SQL_ADD.  
  
-   Les drapeaux d’option doivent être pris en charge dans la version de l’ODBC prise en charge par le conducteur. Par exemple, *InfoType* dans **SQLGetInfo** ne peut pas être SQL_ASYNC_MODE (introduit dans ODBC 3.0) lorsque vous appelez un conducteur ODBC 2.0.  
  
-   Les nombres de colonnes et de paramètres doivent être supérieurs à 0 ou supérieurs ou égaux à 0, selon la fonction. Le conducteur doit vérifier la limite supérieure de ces valeurs d’argumentation en fonction de l’ensemble de résultats actuel ou de l’énoncé SQL.  
  
-   Les arguments de longueur/indicateur et les arguments de longueur de mémoire tampon de données doivent contenir des valeurs appropriées. Par exemple, l’argument qui spécifie la longueur d’un nom de table dans **SQLColumns** (*NameLength3*) doit être SQL_NTS ou une valeur supérieure à 0; *BufferLength* dans **SQLDescribeCol** doit être supérieur ou égal à 0. Le conducteur pourrait également avoir besoin de vérifier ces arguments. Par exemple, il peut vérifier que *NameLength3* est inférieur ou égal à la longueur maximale d’un nom de table dans la source de données.
