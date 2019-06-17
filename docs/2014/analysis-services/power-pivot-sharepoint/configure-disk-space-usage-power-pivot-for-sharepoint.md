---
title: Configurer l’utilisation de l’espace disque (PowerPivot pour SharePoint) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 201a3fda-f162-45d7-bf39-74dcb92fd0e6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fc45827a349dc38054db98e3a435f18a42bdaa0f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66071808"
---
# <a name="configure-disk-space-usage-powerpivot-for-sharepoint"></a>Configurer l'utilisation de l'espace disque (PowerPivot pour SharePoint)
  Un déploiement PowerPivot pour SharePoint utilise l'espace disque de l'ordinateur hôte pour mettre en cache des bases de données PowerPivot afin d'accélérer les rechargements. Chaque base de données PowerPivot chargée en mémoire est d'abord mise en cache sur disque afin qu'elle puisse être rechargée rapidement par la suite pour de nouvelles interrogations de données. Par défaut, PowerPivot pour SharePoint utilise tout l'espace disque disponible pour mettre en cache ses bases de données, mais peut modifier ce comportement en définissant des propriétés qui limitent la quantité d'espace disque utilisée.  
  
 Cette rubrique explique comment définir les limites sur l'utilisation de l'espace disque.  
  
 Cette rubrique ne fournit pas d'aide pour la gestion de l'espace disque des bases de données PowerPivot (incorporées dans des classeurs Excel) stockées dans des bases de données de contenus. Les bases de données PowerPivot peuvent être volumineuses, et grever ainsi par de nouvelles demandes sur la capacité de stockage de la batterie. De plus, si le contrôle de version est activé, vous pouvez avoir facilement plusieurs copies des données dans la même base de données de contenus, augmentant ainsi encore la quantité d'espace disque requise pour le stockage des contenus. Bien que les bases de données PowerPivot soient à prendre sérieusement en compte pour la gestion du disque, elles ne peuvent pas être gérées indépendamment des autres contenus que vous stockez dans une batterie de serveurs SharePoint. Vous devez surveiller attentivement l'espace disque au fur et à mesure que votre entreprise augmente son utilisation des classeurs PowerPivot. Vous pouvez également suivre l'activité des classeurs PowerPivot dans le tableau de bord de gestion PowerPivot et supprimer les classeurs qui ne sont plus utilisés.  
  
## <a name="how-powerpivot-for-sharepoint-manages-cached-databases"></a>Comment PowerPivot pour SharePoint gère les bases de données mises en cache  
 Pour gérer son cache, le service système PowerPivot exécute à intervalles réguliers une tâche en arrière-plan afin de nettoyer les bases de données inutilisées ou obsolètes dont des versions plus récentes existent dans une bibliothèque de contenu. L'objectif du travail de nettoyage est de décharger les bases de données inactives de la mémoire et de supprimer les bases de données inutilisées et mises en cache du système de fichiers. Le travail de nettoyage fait partie de la maintenance à long terme et garantit que les bases de données ne restent pas indéfiniment sur le système. Sur un serveur actif, les bases de données peuvent être supprimées plus souvent en raison de la sollicitation de la mémoire sur le serveur, de leur suppression dans SharePoint, ou de la présence de versions plus récentes dans une bibliothèque de contenu.  
  
 Bien que vous ne puissiez pas planifier le travail de nettoyage, vous pouvez personnaliser la gestion des fichiers du cache en définissant des propriétés de configuration du serveur qui effectuent les opérations suivantes :  
  
-   Fixer des limites à la quantité d'espace disque utilisée par le cache.  
  
-   Spécifier la quantité de données à supprimer lorsque l'espace disque maximal est atteint.  
  
## <a name="how-to-check-disk-space-usage"></a>Comment vérifier l'utilisation de l'espace disque  
 PowerPivot pour SharePoint est installé sur les serveurs d'applications dans une batterie de serveurs SharePoint. Chaque installation a un répertoire de données qui inclut un dossier de sauvegarde. Le dossier de sauvegarde contient tous les fichiers de données qui sont mis en cache par l'instance Analysis Services sur l'ordinateur. Par défaut, le dossier de sauvegarde se trouve à l'emplacement suivant :  
  
 `%drive%:\Program Files\Microsoft SQL Server\MSAS10_50.PowerPivot\OLAP\Backup\Sandboxes\<serviceApplicationName>`  
  
 Pour vérifier combien d'espace disque total est utilisé par le cache, vous devez vérifier la taille du dossier de sauvegarde. Il n'y a aucune propriété dans l'Administration centrale qui surveille le taille actuelle du cache.  
  
 Le dossier de sauvegarde fournit le stockage du cache commun pour une base de données PowerPivot chargée en mémoire sur l'ordinateur local. Si plusieurs applications de service PowerPivot sont définies dans votre batterie de serveurs, n'importe laquelle d'entre elles peut utiliser le serveur local pour charger et mettre en cache par la suite les données PowerPivot. Le chargement et la mise en cache des données sont des opérations de serveur Analysis Services. Ainsi, l'utilisation de l'espace disque total est gérée au niveau de l'instance Analysis Services, dans le dossier de sauvegarde. Des paramètres de configuration qui limitent l'utilisation de l'espace disque sont par conséquent définis sur l'instance unique de SQL Server Analysis Services qui s'exécute sur un serveur d'applications SharePoint.  
  
 Le cache contient uniquement des bases de données PowerPivot. Les bases de données PowerPivot sont stockées dans plusieurs fichiers sous un dossier parent unique (le dossier de sauvegarde). Étant donné que les bases de données PowerPivot sont destinées à être utilisées comme données internes dans un classeur Excel, les noms de la base de données sont basés sur GUID plutôt que descriptifs. Un dossier GUID sous  **\<serviceApplicationName >** est le dossier parent d’une base de données PowerPivot. Lorsque les bases de données PowerPivot sont chargées sur le serveur, des dossiers supplémentaires sont créés pour chaque base de données.  
  
 Étant donné que les données PowerPivot peuvent être chargées sur toute instance Analysis Services dans une batterie, les mêmes données peuvent également être mises en cache sur plusieurs ordinateurs dans la batterie. Cette pratique améliore les performances en ce qui concerne l'utilisation de l'espace disque, mais présente l'inconvénient de ralentir l'accès aux données, car celui-ci est plus rapide si les informations sont déjà disponibles sur le disque.  
  
 Pour réduire immédiatement la consommation d'espace disque, vous pouvez arrêter le service, puis supprimer une base de données PowerPivot du dossier de sauvegarde. La suppression manuelle des fichiers est une mesure temporaire, car une copie plus récente de la base de données sera mise en cache la prochaine fois que les données PowerPivot seront interrogées. Parmi les solutions permanentes figure la limitation de l'espace disque utilisé par le cache.  
  
 Au niveau du système, vous pouvez créer des alertes par courrier électronique qui vous informent lorsque l'espace disque est faible. Microsoft System Center inclut une fonctionnalité d'alerte par courrier électronique. Vous pouvez également utiliser le Gestionnaire de ressources du serveur de fichiers, le Planificateur de tâches ou un script PowerShell pour configurer des alertes. Les liens suivants fournissent des informations utiles pour la définition de notifications relatives à l'espace disque insuffisant :  
  
-   [Quelles sont les nouveautés dans le Gestionnaire de ressources du serveur de fichiers](https://technet.microsoft.com/library/hh831746.aspx) (https://technet.microsoft.com/library/hh831746.aspx).  
  
-   [Guide pas à pas de File Server Resource Manager pour Windows Server 2008 R2](https://go.microsoft.com/fwlink/?LinkID=204875) (https://go.microsoft.com/fwlink/?LinkID=204875).  
  
-   [Définition des alertes d’espace disque faible sur Windows Server 2008](https://go.microsoft.com/fwlink/?LinkID=204870) ( https://go.microsoft.com/fwlink/?LinkID=204870).  
  
## <a name="how-to-limit-the-amount-of-disk-space-used-for-storing-cached-files"></a>Comment limiter la quantité d'espace disque utilisée pour le stockage des fichiers mis en cache  
  
1.  Dans l'Administration centrale, sous Gestion des applications, cliquez sur **Gérer les services sur le serveur**.  
  
2.  Cliquez sur **SQL Server Analysis Services**.  
  
     Notez que les limites sont définies sur l'instance Analysis Services qui s'exécute sur le serveur physique, et pas au niveau de l'application de service. Toutes les applications de service qui utilisent l'instance Analysis Services locale sont soumises à la limite d'espace disque maximal unique définie pour cette instance.  
  
3.  Dans Utilisation du disque, attribuez une valeur (en gigaoctets) pour **Espace disque total** pour définir la quantité maximale d’espace utilisé pour la mise en cache. La valeur par défaut est 0, ce qui permet à Analysis Services d'utiliser tout l'espace disque disponible.  
  
4.  Utilisation des disques, dans le **supprimer mises en cache des bases de données dans des « n » dernières heures** , à spécifier les critères utilisés dernièrement pour vider le cache lorsque l’espace disque atteint la limite maximale.  
  
     La valeur par défaut est de 4 heures, ce qui signifie que toutes les bases de données qui ont été inactives pendant 4 heures ou plus sont supprimées du système de fichiers. Les bases de données inactives mais toujours en mémoire sont déchargées, puis supprimées du système de fichiers.  
  
## <a name="how-to-limit-how-long-a-database-is-kept-in-the-cache"></a>Comment limiter la durée de conservation dans le cache d'une base de données  
  
1.  Dans Administration centrale, sous Gestion des applications, cliquez sur **Gérer les applications de service**.  
  
2.  Cliquez sur **Application de Service PowerPivot par défaut** pour ouvrir le tableau de bord de gestion.  
  
3.  Dans Actions, cliquez sur **Configurer les paramètres d'application de service**.  
  
4.  Dans la section Cache disque, vous pouvez spécifier combien de temps une base de données inactive reste en mémoire pour servir les nouvelles demandes (par défaut, 48 heures) et combien de temps elle reste dans le cache (par défaut, 120 heures).  
  
     L'option**Conserver la base de données inactive dans la mémoire** spécifie pendant combien de temps une base de données inactive reste en mémoire pour servir les nouvelles demandes de données. Une base de données active est toujours conservée en mémoire tant que vous l'interrogez ; lorsqu'elle n'est plus active, le système la conserve en mémoire pour une période supplémentaire au cas où ces données seraient interrogées ultérieurement.  
  
     Étant donné que les bases de données PowerPivot sont d'abord mises en cache, puis chargées en mémoire, les fichiers de base de données consomment immédiatement l'espace disque. Toutefois, tant que la base de données est active (et pendant les 48 heures qui suivent), toutes les demandes sont dirigées en premier vers la base de données en mémoire, en ignorant la base de données mise en cache. Après 48 heures d'inactivité, le fichier est déchargé de la mémoire, mais reste dans le cache où il peut être rechargé rapidement si une nouvelle demande de connexion à ces données est interceptée par l'instance de serveur PowerPivot locale. Les demandes de connexion à une base de données inactive sont servies à partir du cache plutôt qu'à partir de la bibliothèque de contenu, afin de réduire l'impact sur les bases de données de contenus.  
  
     Il est important de noter que la bibliothèque de contenu est le seul emplacement permanent pour les bases de données PowerPivot. Les copies mises en cache sont utilisées uniquement si la base de données dans la bibliothèque est la même que la copie sur le disque.  
  
     L'option**Conserver la base de données inactive dans le cache** spécifie combien de temps une base de données inactive reste dans le système de fichiers après qu'elle a été déchargée de la mémoire. Le travail de nettoyage utilise ce paramètre pour déterminer les fichiers à supprimer. Toutes les bases de données PowerPivot qui sont inactives pendant 168 heures (48 heures en mémoire et 120 heures dans le cache) sont supprimées du disque par le travail de nettoyage.  
  
5.  Cliquez sur **OK** pour enregistrer vos modifications.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Une installation PowerPivot pour SharePoint fournit des règles d'intégrité afin que vous puissiez prendre des actions correctives lorsque des problèmes d'intégrité du serveur, de configuration ou de disponibilité sont détectés. Certaines de ces règles utilisent des paramètres de configuration pour déterminer les conditions sous lesquelles les règles d'intégrité sont déclenchées. Si vous administrez activement les performances du serveur, vous pouvez également consulter ces paramètres pour vous assurer que les valeurs par défaut utilisées sont adaptées à votre système. Pour plus d’informations, consultez [configurer des règles d’intégrité de PowerPivot -](configure-power-pivot-health-rules.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Administration et configuration d’un serveur PowerPivot dans l’Administration centrale](power-pivot-server-administration-and-configuration-in-central-administration.md)  
  
  
