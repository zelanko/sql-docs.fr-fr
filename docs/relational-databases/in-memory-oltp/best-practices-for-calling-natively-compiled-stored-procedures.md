---
title: Bonnes pratiques - Procédures stockées compilées nativement
description: Découvrez les meilleures pratiques pour les procédures stockées compilées en mode natif qui sont généralement utilisées dans les parties critiques des performances d’une application.
ms.custom: seo-dt-2019
ms.date: 03/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: f39fc1c7-cfec-4a95-97f6-6b95954694b
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: bc9fffa0c2b916163e0b9e8698cdf1f7df59667a
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85723386"
---
# <a name="best-practices-for-calling-natively-compiled-stored-procedures"></a>Meilleures pratiques pour appeler des procédures stockées compilées en mode natif
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  Les procédures stockées compilées en mode natif sont les suivantes :  
  
-   utilisées en général dans les parties ayant un impact sur les performances d'une application ;  
  
-   exécutées fréquemment ;  
  
-   réputées très rapides.  
  
 L'avantage lié à l'utilisation d'une procédure stockée compilée en mode natif augmente avec le nombre de lignes et la quantité de logique qui est traitée par la procédure. Par exemple, une procédure stockée compilée en mode natif présentera de meilleures performances si elle utilise un ou plusieurs des éléments suivants :  
  
-   Agrégation.  
  
-   jointures de boucles imbriquées ;  
  
-   opérations de sélection, insertion, mise à jour et suppression en plusieurs instructions ;  
  
-   expressions complexes ;  
  
-   logique procédurale, par exemple des instructions conditionnelles et des boucles.  
  
 Si vous devez traiter une seule ligne, l'utilisation d'une procédure stockée compilée en mode natif peut ne pas fournir un avantage en matière de performances.  
  
 Pour éviter que le serveur soit contraint de mettre en correspondance les noms des paramètres et les types de conversion :  
  
-   Faites correspondre les types de paramètres transmis à la procédure avec les types dans la définition de la procédure.  
  
-   Utilisez des paramètres (sans nom) ordinaux lorsque vous appelez des procédures stockées compilées en mode natif. Pour une exécution optimale, n'utilisez pas de paramètres nommés.  
  
 L’utilisation de paramètres inefficaces avec des procédures stockées compilées en mode natif peut être détectée par le XEvent **natively_compiled_proc_slow_parameter_passing** :
 - Types incompatibles : **reason=parameter_conversion**
 - Paramètres nommés : **reason=named_parameters**
 - Valeurs PAR DÉFAUT : **reason=default** 
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées compilées en mode natif](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)  
