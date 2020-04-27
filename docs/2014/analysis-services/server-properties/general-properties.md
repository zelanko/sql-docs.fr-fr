---
title: Propriétés générales | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- IdleConnectionTimeout property
- InstanceVisible property
- TempDir property
- AdminTimeout property
- MinIdleSessionTimeout property
- MaxIdleSessionTimeout property
- IdleOrphanSessionTimeout property
- BackupDir property
- CommitTimeout property
- ExternalCommandTimeout property
- Enabled property
- ForceCommitTimeout property
- Port property
- CoordinatorShutdownMode property
- ServerTimeout property
- AllowedBrowsingFolders property
- CoordinatorCancelCount property
- DataDir property
- CoordinatorQueryMaxThreads property
- CoordinatorExecutionMode property
- ExternalConnectionTimeout property
- CollationName property
- EnableFast1033Locale property
- CoordinatorBuildMaxThreads property
- Language property
- StatisticsStoreSize property
- RepositoryConnectionString property
ms.assetid: 88a8117c-396a-469f-a62d-c6f262504021
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6b833fe2710ce04cb4a0c8b08fedc9a882c19add
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66069029"
---
# <a name="general-properties"></a>Propriétés générales
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] prend en charge les propriétés de serveur répertoriées dans les tableaux suivants. Cette rubrique décrit les propriétés de serveur qui se trouvent dans le fichier msmdsrv.ini et qui ne font pas l'objet d'une section spécifique, traitant par exemple de la sécurité, du réseau ou de ThreadPool. Pour plus d'informations sur les autres propriétés de serveur et la façon de les configurer, consultez [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).  
  
 **S’applique à :** mode serveur multidimensionnel et tabulaire, sauf indication contraire  
  
## <a name="non-specific-category"></a>Catégorie non spécifique  
 `AdminTimeout`  
 Propriété dont la valeur est un entier 32 bits signé qui définit le délai d'attente de l'administrateur en secondes. Il s'agit d'une propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 La valeur par défaut de cette propriété, zéro (0), indique l'absence de délai d'attente.  
  
 `AllowedBrowsingFolders`  
 Propriété de type chaîne qui spécifie dans une liste délimitée les dossiers qui peuvent être parcourus en enregistrant, en ouvrant, puis en recherchant les fichiers dans les boîtes de dialogue Analysis Services. Le compte de service Analysis Services doit disposer d'autorisations de lecture et d'écriture sur tous les dossiers que vous ajoutez à la liste.  
  
 `BackupDir`  
 Propriété de type chaîne qui identifie le nom du répertoire dans lequel les fichiers de sauvegarde sont stockés par défaut, dans le cas où aucun chemin d’accès n’est spécifié dans le cadre de la commande de sauvegarde.  
  
 `CollationName`  
 Propriété de type chaîne qui identifie le classement du serveur. Pour plus d’informations, consultez [Langues et classements &#40;Analysis Services&#41;](../languages-and-collations-analysis-services.md).  
  
 `CommitTimeout`  
 Propriété dont la valeur est un entier qui spécifie le temps (en millisecondes) pendant lequel le serveur attend pour acquérir un verrou d'écriture afin de valider une transaction. Une période d'attente est souvent nécessaire, car le serveur doit attendre la libération d'autres verrous avant de pouvoir accepter un verrou d'écriture qui valide la transaction.  
  
 La valeur par défaut de cette propriété, zéro (0), indique que le serveur attend indéfiniment. Pour plus d’informations sur les propriétés associées au verrou, consultez le [guide des opérations de SQL Server 2008 R2 Analysis Services](https://go.microsoft.com/fwlink/?LinkID=225539).  
  
 `CoordinatorBuildMaxThreads`  
 Propriété dont la valeur est un entier 32 bits signé qui spécifie le nombre maximal de threads alloués à la génération des index de partition. Augmentez cette valeur si vous souhaitez accélérer l'indexation des partitions au prix d'une plus grande consommation de mémoire. Pour plus d’informations sur cette propriété, consultez le [guide des opérations de SQL Server 2008 R2 Analysis Services](https://go.microsoft.com/fwlink/?LinkID=225539).  
  
 `CoordinatorCancelCount`  
 Propriété dont la valeur est un entier 32 bits signé qui spécifie la fréquence selon laquelle le serveur doit vérifier si un événement d'annulation s'est produit (en fonction d'un nombre d'itérations interne). Diminuez ce nombre si vous souhaitez augmenter la fréquence de ces vérifications au détriment des performances générales.  
  
 `CoordinatorCancelCount` est ignoré en mode serveur tabulaire.  
  
 `CoordinatorExecutionMode`  
 Propriété dont la valeur est un entier 32 bits signé qui spécifie le nombre maximal d'opérations parallèles que le serveur essaiera d'effectuer, notamment les opérations de traitement et d'interrogation. Zéro (0) indique que le serveur décidera lui-même, en fonction d'un algorithme interne. Un nombre positif indique le nombre maximal d'opérations au total. Un nombre négatif (précédé du signe moins) indique le nombre maximal d'opérations par processeur.  
  
 `CoordinatorExecutionMode` est ignoré en mode serveur tabulaire.  
  
 La valeur par défaut de cette propriété, -4, indique que le serveur est limité à quatre opérations parallèles par processeur. Pour plus d’informations sur cette propriété, consultez le [guide des opérations de SQL Server 2008 R2 Analysis Services](https://go.microsoft.com/fwlink/?LinkID=225539).  
  
 `CoordinatorQueryMaxThreads`  
 Propriété dont la valeur est un entier 32 bits signé qui spécifie le nombre maximal de threads par segment de partition durant la résolution des requêtes. Moins il y a d'utilisateurs simultanés, plus cette valeur peut être élevée, au prix d'une plus grande consommation de mémoire. Inversement, il peut s'avérer nécessaire de diminuer cette valeur s'il y a un grand nombre d'utilisateurs simultanés.  
  
 `CoordinatorShutdownMode`  
 Propriété booléenne qui définit le mode d'arrêt du coordinateur. Il s'agit d'une propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `DataDir`  
 Propriété de type chaîne qui spécifie le nom du répertoire où les données sont stockées.  
  
 `DeploymentMode`  
 Détermine le contexte opérationnel d'une instance de serveur Analysis Services. Cette propriété est appelée « mode serveur » dans les boîtes de dialogue, les messages et la documentation. Cette propriété est configurée par le programme d'installation de SQL Server selon le mode serveur que vous avez sélectionné en installant Analysis Services. Cette propriété doit être considérée uniquement comme une propriété interne, toujours à l'aide de la valeur spécifiée par le programme d'installation.  
  
 Les valeurs valides pour cette propriété sont les suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|0|Il s'agit de la valeur par défaut. Elle spécifie le mode multidimensionnel, utilisé pour servir les bases de données multidimensionnelles qui utilisent le stockage MOLAP, HOLAP et ROLAP, ainsi que les modèles d'exploration de données.|  
|1|Spécifie des instances d'Analysis Services installées dans le cadre d'un déploiement PowerPivot pour SharePoint. Ne modifiez pas la propriété du mode de déploiement de l'instance Analysis Services qui fait partie d'une installation PowerPivot pour SharePoint. Les données PowerPivot ne s'exécuteront plus sur le serveur si vous modifiez le mode.|  
|2|Spécifie le mode tabulaire utilisé pour héberger les bases de données model tabulaires qui utilisent le stockage en mémoire ou le stockage DirectQuery.|  
  
 Chaque mode est exclusif pour l'autre. Un serveur configuré pour le mode tabulaire ne peut pas exécuter des bases de données Analysis Services qui contiennent des cubes et des dimensions. Si le matériel informatique sous-jacent peut prendre cela en charge, vous pouvez installer plusieurs instances d'Analysis Services sur le même ordinateur et configurer chaque instance pour utiliser un mode de déploiement différent. Souvenez-vous qu'Analysis Services est une application qui consommée beaucoup de ressources. Le déploiement de plusieurs instances sur le même système est recommandé uniquement pour les serveurs haut de gamme.  
  
 `EnableFast1033Locale`  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `ExternalCommandTimeout`  
 Propriété dont la valeur est un entier qui spécifie le délai d'attente en secondes des commandes envoyées aux serveurs externes, notamment les sources de données relationnelles et les serveurs [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] externes.  
  
 La valeur par défaut de cette propriété est 3600 (secondes).  
  
 `ExternalConnectionTimeout`  
 Propriété dont la valeur est un entier qui spécifie le délai d’attente en secondes de la création des connexions aux serveurs externes, notamment les sources de données relationnelles et les serveurs [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] externes. Cette propriété est ignorée si un délai de connexion est spécifié dans la chaîne de connexion.  
  
 La valeur par défaut de cette propriété est 60 (secondes).  
  
 `ForceCommitTimeout`  
 Propriété dont la valeur est un entier qui spécifie le temps, en millisecondes, pendant lequel une opération de validation d'écriture doit attendre avant l'annulation d'autres commandes qui ont précédé la commande actuelle, notamment les requêtes en cours. Cela permet à la transaction de validation de continuer en annulant les opérations de priorité la plus faible, telles que les requêtes.  
  
 La valeur par défaut de cette propriété, 30 secondes (30 000 millisecondes), indique que l'annulation d'autres commandes ne sera pas forcée tant que la transaction de validation n'a pas attendu 30 secondes.  
  
> [!NOTE]  
>  Les requêtes et les processus annulés par cet événement entraînent l’affichage du message d’erreur suivant : «`Server: The operation has been cancelled`».  
  
 Pour plus d’informations sur cette propriété, consultez le [guide des opérations de SQL Server 2008 R2 Analysis Services](https://go.microsoft.com/fwlink/?LinkID=225539).  
  
> [!IMPORTANT]  
>  `ForceCommitTimeout` s'applique aux commandes de traitement de cube et aux opérations d'écriture différée.  
  
 `IdleConnectionTimeout`  
 Propriété dont la valeur est un entier qui spécifie le délai, en secondes, pour les connexions qui sont inactives.  
  
 La valeur par défaut de cette propriété, zéro (0), indique que le serveur ne ferme pas les connexions inactives.  
  
 `IdleOrphanSessionTimeout`  
 Propriété dont la valeur est un entier qui définit le laps de temps, exprimé en secondes, pendant lequel les sessions orphelines sont conservées dans la mémoire du serveur. Une session orpheline est une session qui n'a plus de connexion associée. La valeur par défaut est 120 secondes.  
  
 `InstanceVisible`  
 Propriété booléenne qui indique si l'instance de serveur est visible pour découvrir des demandes d'instance de service SQL Server Browser. La valeur par défaut est True. Si vous affectez la valeur False, l'instance n'est pas visible pour SQL Server Browser.  
  
 `Language`  
 Propriété de type chaîne qui définit la langue, notamment pour les messages d'erreur et la mise en forme des nombres. Cette propriété a priorité sur la propriété CollationName.  
  
 La valeur par défaut de cette propriété est vide, ce qui indique que la langue est définie par la propriété CollationName.  
  
 `LogDir`  
 Propriété de type chaîne qui spécifie le nom du répertoire qui contient les journaux du serveur. Cette propriété s'applique uniquement si vous utilisez des fichiers sur disque pour l'enregistrement, au lieu de tables de base de données (comportement par défaut).  
  
 `MaxIdleSessionTimeout`  
 Propriété dont la valeur est un entier qui définit le délai d'attente maximal des sessions inactives, exprimé en secondes. La valeur par défaut est zéro (0), ce qui indique que les sessions n’ont jamais dépassé le délai d’attente. Toutefois, les sessions inactives seront quand même supprimées si le serveur est soumis à des contraintes de ressources.  
  
 `MinIdleSessionTimeout`  
 Propriété dont la valeur est un entier qui définit le délai d'attente minimal des sessions inactives, exprimé en secondes. La valeur par défaut est 2700 secondes. Une fois ce délai expiré, le serveur est autorisé à mettre fin à la session inactive, mais il ne le fera que si de la mémoire est requise.  
  
 `Port`  
 Propriété dont la valeur est un entier qui définit le numéro de port sur lequel le serveur sera à l'écoute des connexions clientes. Si cette propriété n'est pas définie, le serveur recherche dynamiquement le premier port inutilisé.  
  
 La valeur par défaut de cette propriété, zéro (0), correspond au port 2383. Pour plus d'informations sur la configuration du port, consultez [Configure the Windows Firewall to Allow Analysis Services Access](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md).  
  
 `ServerTimeout`  
 Entier qui spécifie le délai d'attente des requêtes, en secondes. La valeur par défaut est 3 600 secondes (ou 60 minutes). Zéro (0) indique qu'aucune requête n'expire.  
  
 `TempDir`  
 Propriété de type chaîne qui spécifie l'emplacement de stockage des fichiers temporaires utilisé lors des opérations de traitement, de restauration et autres. La valeur par défaut de cette propriété est déterminée par l'installation. Si elle n'est pas spécifiée, la valeur par défaut est le répertoire Data.  
  
## <a name="requestprioritization-category"></a>Catégorie RequestPrioritization  
 `Enabled`  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `StatisticsStoreSize`  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer les propriétés du serveur dans Analysis Services](server-properties-in-analysis-services.md)   
 [Déterminer le mode serveur d'une instance Analysis Services](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
