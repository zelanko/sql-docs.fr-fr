---
title: Options de mise à niveau de recherche en texte intégral | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- Full-Text Search
- Upgrade options, Full-Text Search
ms.assetid: 16c9376b-5fbb-4495-a429-06a2493849c9
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 575105d61446f2fd272e4087457e7762c1abb2e8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66095085"
---
# <a name="full-text-search-upgrade-options"></a>Options de mise à niveau de recherche en texte intégral
  Utilisez la page des options de mise à niveau de recherche en texte intégral de l'Assistant Installation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour sélectionner l'option de mise à niveau de recherche en texte intégral à utiliser pour les bases de données que vous mettez actuellement à niveau.  
  
 Dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] , chaque index de recherche en texte intégral réside dans un catalogue de texte intégral qui appartient à un groupe de fichiers, a un chemin d'accès physique et est traité en tant que fichier de base de données. Maintenant, un catalogue de texte intégral est un concept unique en son virtuel objet logique-qui fait référence à un groupe d’index de recherche en texte intégral. Par conséquent, un nouveau catalogue de texte intégral n'est pas traité en tant que fichier de base de données avec un chemin d'accès physique. Toutefois, un nouveau groupe de fichiers est créé sur le même disque pendant la mise à niveau de tout catalogue de texte intégral qui contient des fichiers de données. Cela maintient le comportement d'E/S de l'ancien disque après la mise à niveau. Tout index de recherche en texte intégral de ce catalogue est placé dans le nouveau groupe de fichiers si le chemin d'accès racine existe. Si l'ancien chemin de catalogue de texte intégral est non valide, la mise à niveau conserve l'index de recherche en texte intégral dans le même groupe de fichiers comme table de base ou, pour une table partitionnée, dans le groupe de fichiers principal.  
  
## <a name="options"></a>Options  
 Lorsque vous effectuez une mise à niveau vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], choisissez l'une des options de mise à niveau de texte intégral ci-dessous.  
  
 **Importer**  
 Les catalogues de texte intégral sont importés. En général, l'importation est considérablement plus rapide que lors d'une reconstruction (rebuild). Par exemple, lorsque vous utilisez un seul processeur, l'importation s'exécute approximativement 10 fois plus vite que lors de la reconstruction. Toutefois, un catalogue de texte intégral importé de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] n'utilise pas les analyseurs lexicaux nouveaux et améliorés, ce qui fait que vous pouvez le cas échéant reconstruire vos catalogues de texte intégral au final.  
  
> [!NOTE]  
>  Le processus de reconstruction peut s'exécuter en mode multithread, et si plus de 10 processeurs sont disponibles, la reconstruction peut s'effectuer plus vite que l'importation si vous la laissez utiliser tous les processeurs.  
  
 Si aucun catalogue de texte intégral n'est disponible, les index de recherche en texte intégral associés sont reconstruits. Cette option est disponible uniquement pour les bases de données [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] .  
  
 Pour plus d'informations sur l'impact de l'importation de l'index de recherche en texte intégral, consultez « Considérations relatives au choix d'une option de mise à niveau », plus loin dans cette rubrique.  
  
 **Reconstruire**  
 Les catalogues de texte intégral sont reconstruits à l'aide des analyseurs lexicaux nouveaux et améliorés. La reconstruction des index peut prendre beaucoup de temps, et une quantité importante de ressources en termes d'UC et de mémoire peut être requise après la mise à niveau.  
  
 **Réinitialiser**  
 Les catalogues de texte intégral sont réinitialisés. Lors de la mise à niveau à partir de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], les catalogues de texte intégral sont supprimés, mais les métadonnées pour les catalogues de texte intégral et les index de recherche en texte intégral sont conservées. Après leur mise à niveau, tous les index de recherche en texte intégral ont le suivi des modifications désactivé et aucune analyse n'est démarrée automatiquement. Le catalogue reste vide tant que vous n'avez pas procédé manuellement à une alimentation complète, au terme de la mise à niveau.  
  
 Toutes ces options de mise à niveau garantissent que les bases de données mises à niveau bénéficient pleinement des améliorations en termes de performances du texte intégral.  
  
## <a name="considerations-for-choosing-a-full-text-upgrade-option"></a>Considérations relatives au choix d'une option de mise à niveau de texte intégral  
 Au moment de choisir l'option de mise à niveau pour votre mise à niveau, tenez compte des éléments suivants :  
  
-   Comment utilisez-vous les analyseurs lexicaux ?  
  
     Le service de recherche en texte intégral dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] inclut de nouveaux analyseurs lexicaux et générateurs de formes dérivées. Ceux-ci peuvent modifier les résultats de requêtes de texte intégral de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] pour un modèle ou scénario de texte spécifique. Par conséquent, la manière dont vous utilisez les analyseurs lexicaux est importante lors du choix d'une option de mise à niveau appropriée :  
  
    -   Si les analyseurs lexicaux de la langue de texte intégral que vous utilisez n'ont pas changé, ou si l'exactitude de rappel n'est pas critique pour vous, l'importation est appropriée. Ultérieurement, si vous rencontrez des problèmes de rappel, vous pouvez effectuer une mise à niveau vers les nouveaux analyseurs lexicaux en reconstruisant vos catalogues de texte intégral.  
  
    -   Si vous tenez à l'exactitude de rappel et que vous utilisez l'un des analyseurs lexicaux qui ont été ajoutés après [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], la reconstruction est appropriée.  
  
-   Certains index de recherche en texte intégral ont-ils été construits sur la base de colonnes clés de texte intégral de type Integer ?  
  
     La reconstruction effectue, dans quelques cas, des optimisations internes qui améliorent le performances des requêtes de l'index de recherche en texte intégral mis à niveau. Spécifiquement, si vous avez des catalogues de texte intégral qui contiennent des index de recherche en texte intégral dont la colonne clé de texte intégral de la table de base correspond à un type de données Integer, la reconstruction permet d'obtenir une performance idéale des requêtes de texte intégral après la mise à niveau. Nous recommandons vivement que vous utilisiez l'option **Reconstruire** dans ce cas.  
  
    > [!NOTE]  
    >  Pour les index de texte intégral dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], nous recommandons que la colonne servant de clé de texte intégral corresponde à un type de données Integer. Pour plus d’informations, consultez [Améliorer les performances des index de recherche en texte intégral](../../relational-databases/indexes/indexes.md).  
  
-   Quelle est la priorité pour obtenir votre instance de serveur en ligne ?  
  
     L'importation ou la reconstruction pendant la mise à niveau mobilise beaucoup de ressources processeur, ce qui retarde la mise à niveau et en ligne du reste de l'instance serveur. Si le fait d'avoir l'instance de serveur en ligne dès que possible est important et si vous êtes disposé à exécuter une alimentation manuelle après la mise à niveau, la **réinitialisation** est appropriée.  
  
## <a name="additional-resources"></a>Ressources supplémentaires  
  
