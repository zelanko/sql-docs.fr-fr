---
title: Se connecter à un serveur d’exploration de données | Documents Microsoft
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- connections
- getting started
ms.assetid: 85962ad6-d840-4bc6-905e-c667c3276944
caps.latest.revision: 25
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 41d478d518ffb4dcf111542dc0eda26573ba0129
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36044626"
---
# <a name="connect-to-a-data-mining-server"></a>Connexion à un serveur d'exploration de données
  ![Bouton connexions](media/misc-connection.gif "bouton connexions")  
  
 Cliquez sur le **connexion** bouton pour sélectionner une connexion existante ou créer une nouvelle connexion à une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 **Pourquoi besoin pour se connecter à un serveur ?**  
  
 Le fait de créer une connexion vous permet d'utiliser les algorithmes d'exploration de données disponibles sur le serveur [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] et d'exploiter au mieux le traitement optimisé du serveur.  
  
 Vous n'êtes pas tenu de conserver les données ou les résultats dans une base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ou une base de données SQL Server. Les compléments d'exploration de données Excel fonctionnent uniquement avec des données stockées dans Excel, ou avec des données auxquelles vous vous connectez en tant que source de données Excel.  
  
## <a name="how-to-create-a-new-connection"></a>Comment créer une nouvelle connexion  
  
1.  Cliquez sur le **connexion** bouton.  
  
2.  Dans le **connexions Analysis Services** boîte de dialogue, cliquez sur **nouveau**.  
  
3.  Dans le **se connecter à Analysis Services** boîte de dialogue, tapez un nom de serveur.  
  
4.  Spécifiez la méthode d'authentification.  
  
5.  Spécifiez le catalogue, ou la base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], où vous stockerez vos modèles d'exploration de données.  
  
    > [!NOTE]  
    >  Si vous n'avez pas encore créé de base de données, vous pouvez utiliser (valeur par défaut) pour créer, puis tester la connexion ; toutefois, vous ne pouvez pas ajouter de modèles d'exploration de données à la connexion par défaut. Avant de créer des modèles d'exploration de données, vous devez créer une connexion à une base de données existante.  
  
6.  Si vous vous connectez au serveur par le biais d'un service Web, tapez le nom d'utilisateur et mot de passe requis par ce service Web.  
  
7.  Attribuez un nom convivial à la nouvelle connexion.  
  
8.  Cliquez sur **tester la connexion** pour vérifier que le serveur est disponible.  
  
## <a name="troubleshooting-connections"></a>Dépannage des connexions  
 Cette section apporte des réponses à certaines questions les plus fréquentes sur les connexions à [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 **J’obtiens un message indiquant « Connexion introuvable ».**  
  
 Si le texte dans la partie inférieure du bouton indique **aucune connexion**, cela signifie que vous n’avez pas créé une connexion à un [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] base de données, ou que la connexion a échoué. Vous pouvez continuer à travailler dans Excel à partir de données issues d'Access ou d'autres sources, mais pour créer un modèle d'exploration de données ou exécuter une requête de prédiction, vous devez disposer d'une connexion active.  
  
 **Supposons que vous n’êtes pas autorisé à utiliser le serveur ?**  
  
 Si vous n’avez pas d’autorisations suffisantes pour stocker vos modèles d’exploration de données sur le serveur, ou si vous souhaitez faire des essais avec l’exploration de données et sans enregistrer votre travail, vous pouvez utiliser les outils d’analyse de Table, qui créent des structures de données temporaires et les modèles temporaires. Vous devez pouvoir enregistrer les modèles temporaires sur le serveur. Demandez à votre administrateur pour permettre l’utilisation de *les modèles d’exploration de données de session* sur le serveur.  
  
 Pour vous assurer que vos modèles sont enregistrés, désactivez l'option permettant d'utiliser des modèles temporaires, ou utilisez les Assistants du Client d'exploration de données. Ces Assistants stockent tous les modèles sur le serveur. Vous devez un accès administratif à la base de données où les modèles sont stockés, nous vous recommandons que vous obtenez l’administrateur de créer une base de données plus particulièrement pour créer des modèles d’exploration de données avec les compléments.  
  
 **J’ai perdu ma connexion ; perdu tout votre travail ?**  
  
 Si vous fermez la connexion au serveur, les résultats et les données ne sont pas perdus, car ils sont stockés dans Excel. Toutefois, si vous avez créé des modèles temporaires, ces modèles sont supprimés du serveur après un court laps de temps. Ainsi, si vous perdez la connexion de façon temporaire, il est possible que les modèles ne soient pas supprimés.  
  
 Les données ou les résultats qui ont été générés ne seront pas perdus, car tous les rapports et tables sont enregistrés dans Excel.  
  
> [!NOTE]  
>  Évitez de vous déconnecter du serveur ou du réseau lorsque le complément est en communication avec le serveur [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Par exemple, évitez toute déconnexion lors de la création d'un modèle ou du traitement des données. Dans certaines situations, cela risque d'endommager vos données.  
  
 **Impossible de me connecter au modèle à l’aide des outils Visio**  
  
 Les modèles d'exploration de données pour Visio ne peuvent pas utiliser de structures et de modèles d'exploration de données temporaires. Pour créer un diagramme de modèle d'exploration de données, le modèle doit être stocké sur un serveur.  
  
 **Comment puis-je surveiller l’utilisation de la connexion ?**  
  
 Le [Trace &#40;Client d’exploration de données pour Excel&#41; ](trace-data-mining-client-for-excel.md) outil crée un journal de toute l’activité entre les compléments et le serveur spécifié.  
  
 Pour activer l’analyse des modèles de session, sélectionnez le **utiliser des modèles de session** option dans le **suivi** boîte de dialogue.  
  
 La trace vous permet d'afficher les commandes DMX et XMLA générées lorsque les modèles et les structures sont créés. Affichez également les requêtes qui ont été envoyées par le client pour générer des résultats et des rapports dans Excel.  
  
 **Qu’est un modèle temporaire ? Comment puis-je enregistrer un modèle temporaire ?**  
  
 Les outils d'analyse de table pour Excel créent, par défaut, des structures de données et des modèles d'exploration de données temporaires. Continuez à parcourir et interroger des modèles temporaires tant que le classeur est ouvert et que vous ne vous déconnectez pas d'[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 Les structures et les modèles que vous avez créés sont supprimés dès que vous fermez le classeur Excel ou si vous modifiez ou mettez fin à votre connexion à [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 Lorsque vous terminez un Assistant dans le client d'exploration de données pour Excel, les modèles sont enregistrés sur le serveur par défaut, mais la dernière page de chaque Assistant offre la possibilité d'utiliser un modèle temporaire. Si vous sélectionnez cette option, la structure et le modèle d'exploration de données que vous avez créés sont tous deux stockés dans un fichier temporaire. Vous pouvez parcourir, gérer et modifier la structure et le modèle tant qu'Excel reste ouvert. Toutefois, une fois qu'Excel est fermé, la structure et les modèles qui lui sont éventuellement associés sont supprimés.  
  
 Vous pouvez également créer explicitement une structure temporaire ou un modèle à l’aide de la **éditeur de requêtes d’avancé d’exploration de données** et en sélectionnant un des modèles DMX. Ajoutez la clause `USE SESSION MODELS` pour spécifier que les objets sont temporaires.   
  
### <a name="creating-backups-of-mining-models-and-structures"></a>Création de sauvegardes de modèles et structures d'exploration de données  
 Pour créer une sauvegarde d’un modèle ou une structure, vous pouvez l’exporter à l’aide de [gérer les modèles &#40;des compléments d’exploration de données SQL Server&#41;](manage-models-sql-server-data-mining-add-ins.md), dans le Client d’exploration de données pour Excel.  
  
 Si vous avez créé un modèle d'exploration de données temporaire, son non est généralement difficile à comprendre, par exemple Table5_593679_TS_62446. Toutefois, vous pouvez utiliser la [Trace &#40;Client d’exploration de données pour Excel&#41; ](trace-data-mining-client-for-excel.md) outil pour découvrir les noms des structures temporaires et les modèles qui ont été créés par les outils d’analyse de Table, puis sauvegarder les à l’aide de  **Gérer les modèles**.  
  
##### <a name="identify-and-export-a-temporary-model"></a>Identifier et exporter un modèle temporaire  
  
1.  Dans le **connexions** groupe du Client d’exploration de données pour Excel, cliquez sur **Trace**.  
  
2.  Consultez le journal des activités de connexion, puis recherchez le modèle en examinant les colonnes et les sorties prévisibles (par exemple).  
  
     Utilisateurs expérimentés : Si vous êtes familiarisé avec DMX ou XMLA, copiez les instructions dans un fichier en vue d'une utilisation ultérieure.  
  
3.  Lorsque vous avez trouvé le nom du modèle temporaire et de structure, ouvrez **gérer le modèle** et sélectionnez le modèle.  
  
4.  Cliquez sur Exporter ce modèle d'exploration de données pour générer un fichier de script à un emplacement que vous spécifiez.  
  
## <a name="see-also"></a>Voir aussi  
 [Se connecter à la Source de données &#40;Client d’exploration de données pour Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md)   
 [Utilitaire de Configuration du serveur &#40;les données des compléments d’exploration de données pour Excel&#41;](server-configuration-utility-data-mining-add-ins-for-excel.md)  
  
  