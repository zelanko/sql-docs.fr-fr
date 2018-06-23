---
title: Présentation des transformations synchrones et asynchrones | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- integration-services
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- transformations [Integration Services], synchronous and asynchronous
- asynchronous transformations [Integration Services]
- data flow components [Integration Services], synchronous and asynchronous
- synchronous transformations [Integration Services]
ms.assetid: 0bc2bda5-3f8a-49c2-aaf1-01dbe4c3ebba
caps.latest.revision: 16
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 2e943eab4aea643762f2ab9553c800211c5a2d9d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36053325"
---
# <a name="understanding-synchronous-and-asynchronous-transformations"></a>Présentation des transformations synchrones et asynchrones
  Pour comprendre la différence entre une transformation synchrone et une transformation asynchrone dans [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], il est plus facile de commencer par examiner une transformation synchrone. Si une transformation synchrone ne répond pas à vos besoins, il est possible que votre conception nécessite une transformation asynchrone.  
  
## <a name="synchronous-transformations"></a>Transformations synchrones  
 Une transformation synchrone traite les lignes entrantes et les transfère dans le flux de données une ligne à la fois. La sortie est synchrone avec l'entrée ; autrement dit, elles se produisent en même temps. Par conséquent, pour traiter une ligne donnée, la transformation n'a pas besoin d'informations sur les autres lignes du jeu de données. Dans l'implémentation réelle, les lignes sont regroupées dans des mémoires tampons lorsqu'elles passent d'un composant à l'autre, mais ces mémoires tampons sont transparentes pour l'utilisateur. Vous pouvez donc considérer que chaque ligne est traitée séparément.  
  
 La transformation de conversion de données est un exemple de transformation synchrone. Pour chaque ligne entrante, elle convertit la valeur dans la colonne spécifiée et transfère la ligne. Chaque opération de conversion discrète est indépendante de toutes les autres lignes dans le jeu de données.  
  
 Dans [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] scripts et de programmation, vous spécifiez une transformation synchrone en recherchant l’ID d’entrée d’un composant et en l’assignant à la `SynchronousInputID` propriété des sorties du composant. Vous indiquez ainsi au moteur de flux de données de traiter chaque ligne de l'entrée et d'envoyer automatiquement chaque ligne aux sorties spécifiées. Si vous souhaitez diriger chaque ligne vers chaque sortie, vous n'avez pas besoin d'écrire du code supplémentaire pour exporter les données. Si vous utilisez la propriété `ExclusionGroup` pour spécifier que les lignes doivent atteindre un groupe de sorties uniquement, comme dans la transformation de fractionnement conditionnel, vous devez appeler la méthode `DirectRow` afin de sélectionner la destination appropriée pour chaque ligne. Lorsque vous disposez d'une sortie d'erreur, vous devez appeler `DirectErrorRow` pour que les lignes présentant un problème soient transmises à la sortie d'erreur au lieu de la sortie par défaut.  
  
## <a name="asynchronous-transformations"></a>Transformations asynchrones  
 Vous pouvez décider que votre conception nécessite une transformation asynchrone lorsqu'il n'est pas possible de traiter chaque ligne indépendamment de toutes les autres. En d'autres termes, vous ne pouvez pas transférer chaque ligne dans le flux de données dès lors qu'elle est traitée. Vous devez plutôt exporter les données de façon asynchrone, c'est-à-dire à un autre moment que l'importation. Par exemple, les scénarios suivants requièrent une transformation asynchrone :  
  
-   Le composant doit acquérir plusieurs mémoires tampons de données avant de pouvoir effectuer leur traitement. La transformation de tri est un exemple dans lequel le composant doit traiter l'ensemble des lignes en une seule opération.  
  
-   Le composant doit combiner des lignes provenant de plusieurs entrées. La transformation de fusion est un exemple dans lequel le composant doit examiner plusieurs lignes de chaque entrée avant de les fusionner dans l'ordre de tri.  
  
-   Il n'existe pas de correspondance univoque entre les lignes d'entrée et les lignes de sortie. La transformation d'agrégation est un exemple dans lequel le composant doit ajouter une ligne à la sortie pour contenir les valeurs d'agrégation calculées.  
  
 Au cours d'opérations de script et de programmation [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], vous pouvez spécifier une transformation asynchrone en assignant la valeur 0 à la propriété `SynchronousInputID` des sorties du composant. . Vous indiquez ainsi au moteur de flux de données de ne pas envoyer automatiquement chaque ligne aux sorties. Puis, vous devez écrire du code pour envoyer explicitement chaque ligne à la sortie appropriée en l'ajoutant au nouveau tampon de sortie créé pour la sortie d'une transformation asynchrone.  
  
> [!NOTE]  
>  Étant donné qu'un composant source doit également ajouter explicitement chaque ligne qu'il lit à partir de la source de données à ses tampons de sortie, une source ressemble à une transformation avec des sorties asynchrones.  
  
 Il serait également possible de créer une transformation asynchrone qui émule une transformation synchrone en copiant explicitement chaque ligne d'entrée vers la sortie. Cette méthode vous permettrait de renommer des colonnes ou convertir des types ou formats de données. Toutefois, cette méthode dégrade les performances. Vous pouvez parvenir aux mêmes résultats mais en bénéficiant de meilleures performances si vous utilisez des composants Integration Services intégrés, tels que Copie de colonnes ou Conversion de données.  
  
![Icône Integration Services (petite)](media/dts-16.gif "icône Integration Services (petite)")**restent jusqu'à la Date avec Integration Services** <br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visitez la page Integration Services sur MSDN](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’une transformation synchrone à l’aide du composant Script](data-flow/transformations/script-component.md)   
 [Création d’une transformation asynchrone à l’aide du composant Script](extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)   
 [Développement d’un composant de transformation personnalisé à sorties synchrones](extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md)   
 [Développement d’un composant de transformation personnalisé avec des sorties asynchrones](extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-asynchronous-outputs.md)  
  
  