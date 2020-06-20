---
title: Comparaison des solutions de script et des objets personnalisés | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- managed tasks [Integration Services]
- Script task [Integration Services], vs. custom managed tasks
- SSIS Script task, vs. custom managed tasks
- custom tasks [Integration Services], scripts
ms.assetid: c0aea822-a21e-44e1-a3d3-8777bd0a1c34
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 18c78f2ba914dc5b65bba9d11de2a697c7038d5c
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84968417"
---
# <a name="comparing-scripting-solutions-and-custom-objects"></a>Comparaison des solutions de script et des objets personnalisés
  Une tâche de script [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ou un composant Script peuvent implémenter un bon nombre des mêmes fonctionnalités possibles dans une tâche managée personnalisée ou un composant de flux de données personnalisé. Voici quelques éléments à considérer pour choisir le type de tâche approprié à vos besoins :  
  
-   Si la configuration ou les fonctionnalités sont propres à un package individuel, vous devez utiliser la tâche de script ou le composant Script au lieu de développer un objet personnalisé.  
  
-   Si les fonctionnalités sont génériques et pourront être utilisées ultérieurement pour d'autres packages et par d'autres développeurs, vous devez créer un objet personnalisé au lieu d'utiliser une solution de script. Vous pouvez utiliser un objet personnalisé dans tout package, alors qu'un script peut uniquement être utilisé dans le package pour lequel il a été créé.  
  
-   Si le code sera réutilisé dans le même package, vous devez envisager de créer un objet personnalisé. La copie de code depuis une tâche de script ou un composant Script vers une autre tâche ou un autre composant en réduit la facilité de gestion en rendant plus difficiles la gestion et la mise à jour des multiples copies du code.  
  
-   Si l'implémentation va changer avec le temps, envisagez d'utiliser un objet personnalisé. Les objets personnalisés peuvent être développés et déployés séparément du package parent, alors qu'une mise à jour apportée à une solution de script requiert le redéploiement du package entier.  
  
![Icône de Integration Services (petite)](../media/dts-16.gif "Icône Integration Services (petite)")  **restez à jour avec Integration Services**<br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visiter la page Integration Services sur MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.  
  
## <a name="see-also"></a>Voir aussi  
 [Extension de packages avec des objets personnalisés](../extending-packages-custom-objects/extending-packages-with-custom-objects.md)  
  
  
