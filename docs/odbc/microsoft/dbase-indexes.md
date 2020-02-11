---
title: Index dBASE | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- DBase indexes [ODBC]
- DBase driver [ODBC], indexes
ms.assetid: fdfa56f5-e324-4ec2-9267-fdf95ab99373
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d9a0a57c3dce920c6d5fbc2510932066cb5a2659
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68096359"
---
# <a name="dbase-indexes"></a>Index dBASE
Le pilote ODBC dBASE ouvre et met à jour automatiquement les fichiers d’index dBASE IV. Vous devez utiliser la boîte de dialogue **Sélectionner les index** qui s’affiche via l’administrateur de la source de données ODBC pour associer les fichiers dBASE III. ndx aux fichiers dBASE.  
  
 Les limitations suivantes s’appliquent à la création d’index dBASE :  
  
-   Tous les noms de colonnes doivent être valides.  
  
-   Toutes les colonnes doivent être dans le même ordre croissant ou décroissant.  
  
-   La longueur d’une colonne de texte unique doit être inférieure à 100 octets.  
  
-   S’il existe plusieurs colonnes, toutes les colonnes doivent être des colonnes de texte et la somme des tailles de colonne doit être inférieure à 100 octets.  
  
-   Les champs Mémo ne peuvent pas être indexés.  
  
-   Un index ne doit pas être spécifié pour l’ensemble de champs actuel (autrement dit, les index dupliqués ne sont pas autorisés).  
  
-   Le nom de l’index doit correspondre à la Convention d’affectation de noms de l’index dBASE. dBASE III requiert que chaque index soit dans un fichier distinct, chacun avec une extension. ndx. Dans dBASE IV, les index sont créés en tant que noms de balises qui sont stockés dans un fichier. MDX unique. Le fichier. MDX a le même nom de base que le fichier de base de données (par exemple, EMP. MDX est le fichier d’index de la base de données EMP. dbf).  
  
-   dBASE définit un index unique dans lequel un seul enregistrement d’un jeu avec des valeurs de clé identiques est ajouté à l’index.
