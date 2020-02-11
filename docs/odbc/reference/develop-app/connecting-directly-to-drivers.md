---
title: Connexion directe aux pilotes | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connecting to driver [ODBC], SQLDriverConnect
- connecting to data source [ODBC], SqlDriverConnect
- SQLDriverConnect function [ODBC], connecting directly to drivers
- connecting to driver [ODBC], drivers
ms.assetid: f86e198f-a088-4401-9106-aa62a0eb8f6e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 44b9de304069849e965fc335e130ae57d9ec8bad
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68083165"
---
# <a name="connecting-directly-to-drivers"></a>Connexion directe à des pilotes
Comme nous l’avons vu dans [choix d’une source de données ou d’un pilote](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md), plus haut dans cette section, certaines applications ne souhaitent pas utiliser une source de données. Au lieu de cela, ils veulent se connecter directement à un pilote. **SQLDriverConnect** offre à l’application la possibilité de se connecter directement à un pilote sans spécifier de source de données. D’un point de vue conceptuel, une source de données temporaire est créée au moment de l’exécution.  
  
 Pour se connecter directement à un pilote, l’application spécifie le mot clé **Driver** dans la chaîne de connexion au lieu du mot clé **DSN** . La valeur du mot clé **Driver** est la description du pilote telle qu’elle est retournée par **SQLDrivers**. Par exemple, supposons qu’un pilote ait la description du pilote Paradox et nécessite le nom d’un répertoire contenant les fichiers de données. Pour se connecter à ce pilote, l’application peut utiliser l’une des chaînes de connexion suivantes :  
  
```  
DRIVER={Paradox Driver};Directory=C:\PARADOX;  
DRIVER={Paradox Driver};  
```  
  
 Avec la première chaîne, le pilote n’a pas besoin d’informations supplémentaires. Avec la deuxième chaîne, le pilote doit demander le nom du répertoire contenant les fichiers de données.
