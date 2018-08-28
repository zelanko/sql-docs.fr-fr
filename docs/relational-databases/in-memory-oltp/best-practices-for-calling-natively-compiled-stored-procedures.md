---
title: Bonnes pratiques pour appeler des procédures stockées compilées en mode natif | Microsoft Docs
ms.custom: ''
ms.date: 03/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: in-memory-oltp
ms.reviewer: ''
ms.suite: sql
ms.technology: in-memory-oltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f39fc1c7-cfec-4a95-97f6-6b95954694bb
caps.latest.revision: 8
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 92ae1c4500b3cdbe90ea0e6caa0d2233afc52423
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43105883"
---
# <a name="best-practices-for-calling-natively-compiled-stored-procedures"></a>Bonnes pratiques pour appeler des procédures stockées compilées en mode natif
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Les procédures stockées compilées en mode natif sont les suivantes :  
  
-   utilisées en général dans les parties ayant un impact sur les performances d'une application ;  
  
-   exécutées fréquemment ;  
  
-   réputées très rapides.  
  
 L'avantage lié à l'utilisation d'une procédure stockée compilée en mode natif augmente avec le nombre de lignes et la quantité de logique qui est traitée par la procédure. Par exemple, une procédure stockée compilée en mode natif présentera de meilleures performances si elle utilise un ou plusieurs des éléments suivants :  
  
-   agrégation ;  
  
-   jointures de boucles imbriquées ;  
  
-   opérations de sélection, insertion, mise à jour et suppression en plusieurs instructions ;  
  
-   expressions complexes ;  
  
-   logique procédurale, par exemple des instructions conditionnelles et des boucles.  
  
 Si vous devez traiter une seule ligne, l'utilisation d'une procédure stockée compilée en mode natif peut ne pas fournir un avantage en matière de performances.  
  
 Pour éviter que le serveur soit contraint de mettre en correspondance les noms des paramètres et les types de conversion :  
  
-   Faites correspondre les types de paramètres transmis à la procédure avec les types dans la définition de la procédure.  
  
-   Utilisez des paramètres (sans nom) ordinaux lorsque vous appelez des procédures stockées compilées en mode natif. Pour une exécution optimale, n'utilisez pas de paramètres nommés.  
  
 L’utilisation de paramètres inefficaces avec des procédures stockées compilées en mode natif peut être détectée par le XEvent **natively_compiled_proc_slow_parameter_passing** :
 - Types incompatibles : **reason=parameter_conversion**
 - Paramètres nommés : **reason=named_parameters**
 - Valeurs PAR DÉFAUT : **reason=default** 
  
## <a name="see-also"></a> Voir aussi  
 [Procédures stockées compilées en mode natif](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)  
