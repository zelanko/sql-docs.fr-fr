---
title: "Comparaison des Solutions de script et des objets personnalisés | Documents Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- managed tasks [Integration Services]
- Script task [Integration Services], vs. custom managed tasks
- SSIS Script task, vs. custom managed tasks
- custom tasks [Integration Services], scripts
ms.assetid: c0aea822-a21e-44e1-a3d3-8777bd0a1c34
caps.latest.revision: 42
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 8d0d387c56513475df9764b0c11f2e8bdb8ed728
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="comparing-scripting-solutions-and-custom-objects"></a>Comparaison des solutions de script et des objets personnalisés
  Une tâche de script [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ou un composant Script peuvent implémenter un bon nombre des mêmes fonctionnalités possibles dans une tâche managée personnalisée ou un composant de flux de données personnalisé. Voici quelques éléments à considérer pour choisir le type de tâche approprié à vos besoins :  
  
-   Si la configuration ou les fonctionnalités sont propres à un package individuel, vous devez utiliser la tâche de script ou le composant Script au lieu de développer un objet personnalisé.  
  
-   Si les fonctionnalités sont génériques et pourront être utilisées ultérieurement pour d'autres packages et par d'autres développeurs, vous devez créer un objet personnalisé au lieu d'utiliser une solution de script. Vous pouvez utiliser un objet personnalisé dans tout package, alors qu'un script peut uniquement être utilisé dans le package pour lequel il a été créé.  
  
-   Si le code sera réutilisé dans le même package, vous devez envisager de créer un objet personnalisé. La copie de code depuis une tâche de script ou un composant Script vers une autre tâche ou un autre composant en réduit la facilité de gestion en rendant plus difficiles la gestion et la mise à jour des multiples copies du code.  
  
-   Si l'implémentation va changer avec le temps, envisagez d'utiliser un objet personnalisé. Les objets personnalisés peuvent être développés et déployés séparément du package parent, alors qu'une mise à jour apportée à une solution de script requiert le redéploiement du package entier.  
  
## <a name="see-also"></a>Voir aussi  
 [Extension de packages avec des objets personnalisés](../../integration-services/extending-packages-custom-objects/extending-packages-with-custom-objects.md)  
  
  
