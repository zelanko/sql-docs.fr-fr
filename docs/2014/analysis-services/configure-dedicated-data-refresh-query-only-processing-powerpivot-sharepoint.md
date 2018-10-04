---
title: Configurer l’actualisation des données uniquement ou le traitement des requêtes uniquement (PowerPivot pour SharePoint) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 5e027605-1086-4941-bb01-f315df8f829b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1c3b42834bc12048680c97465810832f5431441d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48168181"
---
# <a name="configure-dedicated-data-refresh-or-query-only-processing-powerpivot-for-sharepoint"></a>Configurer un traitement d'actualisation des données uniquement ou de requêtes uniquement (PowerPivot pour SharePoint)
  En mode intégré SharePoint, une instance de serveur Analysis Services peut être configurée pour prendre en charge un type spécifique de demande de traitement, comme l'actualisation des données ou le traitement des requêtes uniquement. Par défaut, les deux types sont activés. Vous pouvez en désactiver un pour créer un moteur d'interrogation dédié ou un serveur d'actualisation des données.  
  
 **[!INCLUDE[applies](../includes/applies-md.md)]**  SharePoint 2010  
  
> [!NOTE]  
>  Dans cette version, il n'existe pas de paramètre de configuration qui permette de limiter l'utilisation de la mémoire ou de l'UC pour les travaux d'actualisation des données ou les requêtes à la demande. Une instance du [!INCLUDE[ssGeminiSrv](../includes/ssgeminisrv-md.md)] utilise toutes les ressources disponibles pour exécuter les requêtes et les travaux d'actualisation des données qu'il gère.  
  
 Cette rubrique contient les sections suivantes :  
  
 [Configurer un mode de traitement](#config)  
  
 [Modifier le nombre de travaux d’actualisation des données qui peuvent s’exécuter en parallèle](#change)  
  
##  <a name="config"></a> Configurer un Mode de traitement  
  
1.  Dans l'Administration centrale, sous Paramètres système, cliquez sur **Gérer les services sur le serveur**.  
  
2.  En haut de la page, sous Serveur, cliquez sur la flèche orientée vers le bas, puis sur **Changer de serveur**.  
  
3.  Sélectionnez le serveur SharePoint où se situe l'instance de serveur Analysis Services à configurer.  
  
4.  Cliquez sur **SQL Server Analysis Services**.  
  
5.  Dans Utilisation de l'instance de service, effectuez l'une des opérations suivantes :  
  
    1.  Désactivez la case à cocher pour **activer le chargement de bases de données en lecture seule** pour désactiver le traitement des requêtes de la demande qui se produit chaque fois qu’un utilisateur ouvre un classeur qui contient des données PowerPivot.  
  
    2.  Désactivez la case à cocher pour **activer le chargement de bases de données pour l’actualisation** pour désactiver l’actualisation planifiée des données.  
  
    > [!NOTE]  
    >  Désactiver l'actualisation des données ne supprime pas les options d'actualisation des données des sites SharePoint. Les utilisateurs propriétaires de classeurs PowerPivot peuvent toujours créer des planifications pour l'actualisation des données, mais aucune actualisation ne sera effectuée sur ce serveur.  
  
6.  Pour les opérations d'actualisation des données, vous pouvez si vous le souhaitez modifier le nombre de travaux d'actualisation simultanés. L'augmentation du nombre de travaux simultanés est recommandée si le serveur est configuré pour l'actualisation des données uniquement ou si le serveur comprend des processeurs supplémentaires. Vous pouvez diminuer le nombre de travaux simultanés si vous souhaitez libérer des ressources système pour d'autres requêtes à la demande.  
  
7.  Enregistrez vos modifications. Le serveur ne validera vos entrées que lorsqu'un événement de traitement se produira. Si vous entrez un nombre non valide pour les travaux simultanés, l'erreur sera détectée et journalisée lors du traitement de la requête suivante.  
  
##  <a name="change"></a> Modifier le nombre de travaux d’actualisation des données qui peuvent s’exécuter en parallèle  
 Un travail d'actualisation des données est une tâche planifiée ajoutée à une file d'attente de traitement gérée et surveillée par une application de service PowerPivot. Un travail est constitué d'informations de planification pour une ou plusieurs sources de données dans un classeur PowerPivot. Un travail distinct est créé pour chaque planification définie. Si un propriétaire de classeur définit une planification pour toutes les sources de données, un seul travail est créé pour toute l'opération d'actualisation des données. Si un propriétaire de classeur crée des planifications individuelles pour des sources de données externes, plusieurs travaux sont créés et exécutés pour effectuer une actualisation des données complète pour ce classeur.  
  
 Vous pouvez augmenter le nombre de travaux d'actualisation des données pouvant s'exécuter simultanément si votre système est capable de traiter la charge supplémentaire.  
  
|Paramètre|Valeurs valides|Description|  
|-------------|------------------|-----------------|  
|Valeur par défaut|Calculées d'après la RAM.|La valeur par défaut est basée sur la quantité de mémoire disponible divisée par 4 gigaoctets. La valeur par défaut est calculée par une formule afin que les paramètres puissent être ajustés selon les capacités du système.<br /><br /> Remarque : Le diviseur de 4 Go a été sélectionné pour l’utilisation de RAM pour un large échantillon de sources de données PowerPivot réelles. Il n'est pas basé sur l'architecture physique ou logique de PowerPivot.|  
|Valeur maximale|Calculées d'après le nombre d'unités centrales.|Le nombre maximal de travaux simultanés que vous pouvez spécifier est basé sur le nombre de processeurs de l'ordinateur. Par exemple, sur un ordinateur quadruple cœur à 4 sockets, le nombre maximal de travaux que vous pouvez exécuter simultanément est 16.|  
  
#### <a name="increasing-the-default-value-to-a-higher-value"></a>Choix d'une valeur par défaut plus élevée  
 Le graphique suivant affiche des combinaisons différentes de RAM et d'UC, ainsi que les valeurs par défaut et maximale obtenues, calculées selon les caractéristiques du système. N'oubliez pas que la valeur par défaut calculée pour le nombre de travaux d'actualisation des données pouvant s'exécuter simultanément est basée sur la mémoire système, tandis que la valeur maximale calculée est basée sur les UC. La dernière colonne indique si vous pouvez augmenter le nombre maximal de travaux simultanés d'actualisation des données.  
  
|RAM réelle (en gigaoctets)|Valeur par défaut calculée|Nombre réel d'UC|Valeur maximale calculée|Augmenter les travaux simultanés ?|  
|---------------------------------|------------------------------|------------------------|------------------------------|-------------------------------|  
|4|1|1|1|Non. Les valeurs par défaut et maximale sont identiques.|  
|4|1|4|4|Oui. Vous pouvez augmenter le nombre de travaux simultanés à 2, 3 ou 4.|  
|8|2|4|4|Oui. Vous pouvez augmenter le nombre de travaux simultanés à 3 ou 4.|  
|16|4|4|4|Non. Les valeurs par défaut et maximale sont identiques.|  
|32|En utilisant la formule qui calcule la valeur par défaut, la valeur par défaut serait 8. Étant donné que la valeur par défaut est plus élevée que la valeur maximale autorisée, la valeur par défaut calculée n'est pas utilisée dans ce cas.|4|4|Non. Bien qu'une RAM importante indiquerait une valeur par défaut de 8 travaux simultanés, un ordinateur comprenant 4 processeurs ne prend en charge qu'un maximum de 4 travaux simultanés.|  
|32|8|8|8|Non.|  
|32|8|16|16|Oui.|  
|64|16|16|16|Non.|  
  
 Étant donné qu'aucune méthode ne permet de savoir à l'avance si plusieurs travaux peuvent s'exécuter correctement en même temps, vous ne devez augmenter le nombre de travaux simultanés qu'après avoir analysé la consommation de mémoire dans le temps et déterminé que la mémoire du serveur est généralement sous-utilisée.  
  
 Chaque travail d'actualisation des données présente des caractéristiques de charge différentes qui varient en fonction du nombre et de la taille des sources de données actualisées. La charge de traitement de plusieurs classeurs ayant une seule source de données avec un petit nombre de lignes est bien plus légère que celle d'un classeur ayant de nombreuses sources de données et de très grands ensembles de lignes.  
  
## <a name="see-also"></a>Voir aussi  
 [Actualisation des données PowerPivot avec SharePoint 2010](powerpivot-data-refresh-with-sharepoint-2010.md)  
  
  
