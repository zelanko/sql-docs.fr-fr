---
title: Configurer les propriétés du serveur dans Analysis Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- SSAS, configuration properties
- Analysis Services, configuration properties
- SQL Server Analysis Services, configuration properties
- configuration options [Analysis Services]
- server properties [Analysis Services]
- properties [Analysis Services], configuration
- properties [Analysis Services]
ms.assetid: 274b89cd-14ed-4666-bc13-eedf1de51e18
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 31c05bbc1be8376144eb191ff28a9cdc6eebdd8a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66068899"
---
# <a name="configure-server-properties-in-analysis-services"></a>Configurer les propriétés du serveur dans Analysis Services
  Un administrateur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] peut modifier les propriétés de configuration par défaut du serveur pour une instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Chaque instance a ses propriétés de configuration propres, qui peuvent être définies de façon indépendante des autres instances présentes sur le même serveur.  
  
 Pour définir les propriétés du serveur, utilisez SQL Server Management Studio ou modifiez le fichier msmdsrv.ini d'une instance spécifique.  
  
 Cette rubrique contient les sections suivantes :  
  
 [Configurer les propriétés du serveur (instance)](#bkmk_config)  
  
 [Référence de propriété de serveur](#bkmk_ref)  
  
##  <a name="configure-server-instance-properties"></a><a name="bkmk_config"></a>Configurer les propriétés du serveur (instance)  
 Les pages de propriétés de SQL Server Management Studio contiennent un sous-ensemble des propriétés disponibles, à savoir celles qui sont le plus susceptible d'être modifiées. Le jeu complet des propriétés se trouve dans le fichier msmdsrv.ini.  
  
> [!NOTE]  
>  Cette rubrique ne documente pas les propriétés de configuration de déploiement dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Pour plus d’informations sur la configuration du déploiement, consultez [spécification des paramètres de configuration pour le déploiement de solutions](../multidimensional-models/deployment-script-files-solution-deployment-config-settings.md).  
  
#### <a name="view-or-set-configuration-properties-in-management-studio"></a>Afficher ou définir les propriétés de configuration dans Management Studio  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connectez-vous à une instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
     Dans l’Explorateur d’objets, cliquez avec le bouton droit sur l’instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , puis cliquez sur **Propriétés**. La page Général apparaît, affichant les propriétés couramment utilisées.  
  
2.  Pour afficher des propriétés supplémentaires, cochez la case **Afficher les propriétés avancées (toutes)** en bas de la page.  
  
     La modification des propriétés du serveur est prise en charge uniquement pour les serveurs en mode multidimensionnel et en mode tabulaire. Si vous avez installé [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)], utilisez toujours les valeurs par défaut à moins qu'un ingénieur du support technique de Microsoft vous conseille de faire autrement.  
  
     Pour obtenir de l’aide sur la façon de résoudre les problèmes opérationnels ou de performances au moyen des propriétés du serveur, consultez le [guide des opérations de SQL Server 2008 R2 Analysis Services](https://go.microsoft.com/fwlink/?LinkID=225539).  
  
     La lecture du livre blanc de Microsoft intitulé [SQL Server 2005 Analysis Services (SSAS) Server Properties](https://go.microsoft.com/fwlink/?LinkID=199102)peut également être utile pour en savoir plus sur les propriétés du serveur (pour la plupart inchangées dans les dernières versions).  
  
    > [!NOTE]  
    >  Certaines propriétés ne peuvent être définies que dans le fichier msmdrsrv.ini. Si la propriété qui vous intéresse n'est pas visible même après affichage des propriétés avancées, vous devrez la modifier directement dans le fichier msmdsrv.ini.  
  
#### <a name="view-or-edit-configuration-properties-in-the-msmdsrvini-file"></a>Afficher ou modifier manuellement les propriétés de configuration dans le fichier msmdsrv.ini  
  
1.  Avant de commencer, vérifiez la propriété **datadir** de la page de propriétés général dans Management Studio pour vérifier l’emplacement des fichiers programme de Analysis Services, y compris le fichier msmdsrv. ini. Vous serez ainsi certain de modifier le bon fichier.  
  
    > [!NOTE]  
    >  Dans une installation par défaut, ce fichier se trouve dans le dossier \Program Files\Microsoft SQL Server\MSAS12.MSSQLSERVER\OLAP\Config.  
  
2.  Créez une sauvegarde du fichier, ce qui vous permettra de le restaurer en cas de besoin.  
  
3.  Utilisez un éditeur de texte pour afficher ou modifier le fichier msmdsrv.ini.  
  
4.  Après avoir enregistré le fichier, vous devez redémarrer le service.  
  
##  <a name="server-property-reference"></a><a name="bkmk_ref"></a>Référence de propriété de serveur  
 Les propriétés de configuration de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sont importantes pour le réglage précis de votre système. Par exemple, vous pouvez adapter le comportement du journal des requêtes à vos besoins en définissant les propriétés pertinentes.  
  
 Les rubriques suivantes expliquent les diverses propriétés de configuration de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] :  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Propriétés générales](general-properties.md)|Les propriétés générales sont des propriétés fondamentales et avancées qui définissent notamment le répertoire de données, le répertoire de sauvegarde et d'autres comportements du serveur.|  
|[Propriétés de l'exploration de données](data-mining-properties.md)|Les propriétés d'exploration de données déterminent les algorithmes d'exploration de données à activer ou à désactiver. Par défaut, tous les algorithmes sont activés.|  
|DSO|DSO n'est plus pris en charge. Les propriétés DSO sont ignorées.|  
|[Propriétés de fonctionnalité](feature-properties.md)|Les propriétés de fonctionnalité se rapportent à des fonctionnalités de produit, le plus souvent de caractère avancé. Il s'agit notamment de propriétés qui contrôlent les liaisons entre les instances de serveur.|  
|[Propriétés du cache de la](filestore-properties.md)|Les propriétés du stockage de fichiers s'adressent uniquement aux utilisateurs expérimentés. Elles contiennent des paramètres avancés de gestion de la mémoire.|  
|[Propriétés du gestionnaire de verrous](lock-manager-properties.md)|Les propriétés du gestionnaire de verrous définissent les comportements du serveur en matière de verrouillage et de délais d'attente. La plupart de ces propriétés s'adressent uniquement aux utilisateurs expérimentés.|  
|[Propriétés du journal](log-properties.md)|Les propriétés du journal contrôlent si des événements sont enregistrés sur le serveur et, dans l'affirmative, à quel emplacement et de quelle façon. Il s'agit en particulier de l'enregistrement des erreurs, des exceptions et des requêtes, de la boîte noire SQL et des traces.|  
|[Propriétés de mémoire](memory-properties.md)|Les propriétés de la mémoire contrôlent la façon dont le serveur utilise la mémoire. Elles s'adressent essentiellement aux utilisateurs expérimentés.|  
|[Propriétés du réseau](network-properties.md)|Les propriétés réseau contrôlent le comportement du serveur en matière de réseau, et contiennent notamment des paramètres XML binaire et de compression. La plupart de ces propriétés s'adressent uniquement aux utilisateurs expérimentés.|  
|[Propriétés OLAP](olap-properties.md)|Les propriétés OLAP contrôlent le traitement des cubes et des dimensions, le traitement différé, la mise en cache des données et le comportement des requêtes. Il s'agit de propriétés fondamentales et de propriétés avancées.|  
|[Propriétés de sécurité](security-properties.md)|La section de la sécurité contient des propriétés fondamentales et avancées qui définissent les autorisations d'accès. Il s'agit de paramètres concernant les administrateurs et les utilisateurs.|  
|[Propriétés du pool de threads](thread-pool-properties.md)|Les propriétés du pool de threads contrôlent le nombre de threads que crée le serveur. Il s'agit essentiellement de propriétés avancées.|  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des instances de Analysis Services](../instances/analysis-services-instance-management.md)   
 [Spécification de paramètres de configuration pour le déploiement de solutions](../multidimensional-models/deployment-script-files-solution-deployment-config-settings.md)  
  
  
