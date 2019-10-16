---
title: Prise en main de Assistant Expérimentation de base de données pour les mises à niveau SQL Server
description: Prise en main de Assistant Expérimentation de base de données
ms.custom: ''
ms.date: 10/22/2018
ms.prod: sql
ms.prod_service: dea
ms.suite: sql
ms.technology: dea
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: HJToland3
ms.author: ajaykar
ms.reviewer: mathoma
ms.openlocfilehash: 9fe162b2a9bc0db4a2a49648eecb76c5802f57c0
ms.sourcegitcommit: 4c75b49599018124f05f91c1df3271d473827e4d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72381771"
---
# <a name="get-started-with-database-experimentation-assistant"></a>Prise en main de Assistant Expérimentation de base de données

Assistant Expérimentation de base de données (DEA) est une solution de test A/B permettant de modifier des environnements SQL Server, tels que des mises à niveau ou de nouveaux index. La DEA vous aide à évaluer la façon dont la charge de travail sur votre serveur source (dans votre environnement actuel) sera exécutée dans votre nouvel environnement. La DEA vous guide tout au long de l’exécution d’un test A/B en effectuant trois étapes : 

- Capture
- Relecture
- Analyse

Cet article vous guide tout au long de ces étapes.

## <a name="capture"></a>Capture

La première étape de SQL Server un test a/B consiste à capturer une trace sur votre serveur source. Le serveur source est généralement le serveur de production. Les fichiers de trace capturent l’intégralité de la charge de travail des requêtes sur ce serveur, y compris les horodateurs. Plus tard, cette trace est relue sur vos serveurs cibles à des fins d’analyse. Le rapport d’analyse fournit des informations sur la différence de performances de la charge de travail entre vos deux serveurs cibles.

Éléments à prendre en considération :

- Avant de commencer la capture de trace, assurez-vous de sauvegarder les bases de données à partir desquelles vous capturez une trace.
- Un utilisateur de DEA doit être configuré pour se connecter à la base de données à l’aide de l’authentification Windows.
- Un compte de service SQL Server nécessite l’accès au chemin du fichier de trace source.
- Pour la DEA afin de déterminer si les performances d’une requête sont améliorées ou détériorées, cette requête doit s’exécuter au moins 15 fois pendant la période de capture.  

Pour capturer une trace sur votre serveur source :

1. Dans la DEA, accédez à **toutes les captures** en sélectionnant l’icône de l’appareil photo dans le menu de gauche.

   ![Menu de navigation gauche](./media/database-experimentation-assistant-get-started/dea-get-started-leftnav.png)

1. Entrez ou sélectionnez les informations suivantes :

   - **Nom**de la trace : nom de fichier du nouveau fichier de trace que vous êtes en train de créer. Évitez un nom de trace qui utilise la Convention d’affectation de noms de fichiers de substitution, par exemple, CaptureName @ no__t-0NNN.
   - **Duration**: durée de la capture.
   - **SQL Server nom**de l’instance : SQL Server instance à partir de laquelle vous souhaitez capturer une trace.
   - **Nom de la base de données**: nom de la base de données sur l’ordinateur exécutant SQL Server dont vous souhaitez capturer une trace. Si le champ n’est pas renseigné, la trace est capturée à partir de toutes les bases de données sur le serveur.
   - **Chemin de stockage du fichier de trace source sur SQL Server ordinateur**: chemin d’accès du dossier où vous souhaitez enregistrer le fichier de trace.

1. Assurez-vous que la base de données cible est sauvegardée. Activez ensuite la case à cocher base de données.
1. Sélectionnez **Démarrer** pour démarrer la capture.

Vous pouvez afficher la progression de votre capture, y compris l’heure de début, la durée et le temps restant. Vous pouvez également démarrer une nouvelle capture en attendant que cette capture se termine. Une fois la capture terminée, utilisez le fichier de trace de sortie pour commencer la deuxième phase : relisez le fichier de trace sur vos serveurs cibles.

Pour obtenir des questions courantes sur la capture de trace, consultez le [Forum aux questions](database-experimentation-assistant-capture-trace.md#frequently-asked-questions-about-trace-capture)sur la capture.

## <a name="replay"></a>Relecture

La deuxième étape de SQL Server un test a/B consiste à relire le fichier de trace qui a été capturé sur vos serveurs cibles. Ensuite, collectez des traces étendues à partir des relectures à des fins d’analyse. 

Vous relisez le fichier de trace sur deux serveurs cibles : un qui imite votre serveur source (cible 1) et un autre qui imite la modification proposée (cible 2). Les configurations matérielles des cibles 1 et 2 doivent être aussi similaires que possible, de sorte que SQL Server pouvez analyser avec précision l’impact sur les performances de vos modifications proposées.

Éléments à prendre en considération :

- Pour exécuter la relecture, vos ordinateurs doivent être configurés pour exécuter des traces Distributed Replay (DReplay). Pour plus d’informations, consultez [configuration du contrôleur et du client Distributed Replay](https://blogs.msdn.microsoft.com/datamigration/distributed-replay-controller-and-client-setup/).
- Veillez à restaurer les bases de données sur vos serveurs cibles à l’aide de la sauvegarde à partir du serveur source.
- La mise en cache des requêtes dans SQL Server peut affecter les résultats de l’évaluation. Nous vous recommandons de redémarrer le service de SQL Server (MSSQLSERVER) dans l’application des services pour améliorer la cohérence dans les résultats de l’évaluation.

Pour relire le fichier de trace :

1. Dans DEA, sélectionnez l’icône de lecture dans le menu de gauche pour accéder à **toutes les relectures**. La liste des relectures antérieures qui s’exécutent pendant la session, le cas échéant, s’affiche. Pour démarrer une nouvelle relecture, sélectionnez **nouvelle relecture**.

1. Entrez ou sélectionnez les informations suivantes :

   - **Nom de la relecture**: nom de fichier de la trace de relecture.
   - **Nom de l’ordinateur contrôleur**: nom de l’ordinateur du contrôleur de Distributed Replay.
   - **Chemin du fichier de trace source sur le contrôleur**: chemin d’accès du fichier de trace source à partir de la [capture](#capture).
   - **SQL Server nom**de l’instance : nom de l’instance de SQL Server sur laquelle relire la trace source.
   - **Chemin de stockage du fichier de trace cible sur SQL Server ordinateur**: chemin d’accès au dossier pour le fichier de trace de relecture résultant.

1. Activez la case à cocher pour restaurer la sauvegarde à partir de la première étape.

1. Sélectionnez **Démarrer** pour démarrer la relecture. 

Vous pouvez afficher l’état de votre relecture. Une fois que vous avez relu le suivi source sur les deux serveurs cibles, vous êtes prêt à générer un rapport d’analyse.

Pour obtenir des questions courantes sur la relecture, consultez le FAQ sur la [relecture](database-experimentation-assistant-replay-trace.md#frequently-asked-questions-about-trace-replay).

## <a name="analysis"></a>Analyse

La dernière étape consiste à générer un rapport d’analyse à l’aide des traces de relecture. Le rapport d’analyse peut vous aider à mieux comprendre les implications sur les performances de la modification proposée.

Éléments à prendre en considération :

- Si un ou plusieurs composants sont manquants, une page conditions préalables avec des liens pour les téléchargements s’affiche lorsque vous essayez de générer un nouveau rapport d’analyse (connexion Internet requise).
- Pour afficher un rapport qui a été généré dans une version antérieure de l’outil, vous devez d’abord mettre à jour le schéma.

Pour générer un rapport d’analyse :

1. Dans le menu de gauche, accédez à **rapports d’analyse**. Connectez-vous à l’ordinateur qui exécute SQL Server où vous stockez vos bases de données de rapports. Une liste de tous les rapports du serveur s’affiche. Pour créer un rapport, sélectionnez **nouveau rapport**.

1. Entrez ou sélectionnez les informations requises pour générer un rapport :

   - **Nom du rapport**: nom du rapport d’analyse à créer.
   - **Trace pour la cible 1 SQL Server**: le chemin d’accès du fichier de trace de la relecture sur la cible 1.
   - **Trace pour la cible 2 SQL Server**: le chemin d’accès du fichier de trace de la relecture sur la cible 2.

1. Sélectionnez **Démarrer** pour générer le rapport. Le nouveau rapport apparaît en haut de la liste. L’icône en regard du rapport devient une coche verte lorsque le rapport a été généré.

À présent, affichez le rapport d’analyse pour obtenir des informations fournies par votre test A/B.

Pour obtenir des questions courantes sur les rapports d’analyse, consultez le FAQ sur l' [analyse](database-experimentation-assistant-create-report.md#frequently-asked-questions-about-analysis-reports).

### <a name="analysis-report"></a>Rapport d’analyse

Sur la première page de votre rapport, les informations de version et de build des serveurs cibles sur lesquels l’expérimentation a été exécutée s’affichent. Vous pouvez utiliser le seuil pour ajuster la sensibilité ou la tolérance de votre analyse de test A/B. Par défaut, le seuil est défini sur 5%. Toute amélioration des performances supérieure ou égale à 5% est catégorisée comme étant **améliorée**. Sélectionnez les options dans le menu déroulant pour évaluer le rapport à l’aide de différents seuils de performances.

![Seuil](https://msdnshared.blob.core.windows.net/media/2017/03/threshold.jpg)

Deux graphiques à secteurs illustrent les implications en termes de performances de la différence entre les deux serveurs cibles pour votre charge de travail. Le graphique de gauche est basé sur le nombre d’exécutions. Le graphique de droite est basé sur des requêtes distinctes. Il existe cinq catégories possibles :

- **Amélioration**: statistiquement, la requête s’est exécutée mieux sur la cible 2 que sur la cible 1.
- **Détérioré**: statistiquement, la requête s’est exécutée pire sur la cible 2 que sur la cible 1.
- **Identique**: il n’existe pas de différence statistique pour la requête entre Target 1 et Target 2.
- **Impossible d’évaluer**: la taille de l’échantillon pour la requête est trop petite pour l’analyse statistique. Pour l’analyse de test A/B, la DEA requiert que les mêmes requêtes aient au moins 30 exécutions sur chaque cible.
- **Erreur**: la requête a erroné au moins une fois sur l’une des cibles.

![Graphique à secteurs](./media/database-experimentation-assistant-get-started/dea-get-started-piechart.png)

Sélectionnez une tranche pour accéder à une catégorie particulière et obtenir des métriques de performances, notamment le secteur **ne peut pas évaluer** le secteur.

La page d’exploration pour une catégorie de modification des performances affiche une liste de requêtes dans cette catégorie. La page d' **erreur** comporte trois onglets :

- **Nouvelles Erreurs**: erreurs qui sont apparues sur la cible 2 mais pas sur la cible 1.
- **Erreurs existantes**: erreurs qui sont apparues sur les cibles 1 et 2.
- **Erreurs résolues**: erreurs qui apparaissaient sur la cible 1 mais pas sur la cible 2.

   ![Page d’erreur](./media/database-experimentation-assistant-get-started/dea-get-started-errorpage.png)

Sélectionnez une requête pour accéder à une page de **Résumé de comparaison** pour cette requête.

La page Résumé de la **comparaison** affiche des statistiques récapitulatives pour cette requête. Le résumé comprend le nombre d’exécutions, la durée moyenne, l’UC moyenne, les lectures/écritures moyennes et le nombre d’erreurs.

![Statistiques de résumé](./media/database-experimentation-assistant-get-started/dea-get-started-summarystats.png)

Si la requête est une requête d’erreur, l’onglet informations sur l' **erreur** affiche plus d’informations sur l’erreur. L’onglet informations sur le **plan de requête** affiche des informations sur les plans de requête utilisés pour la requête sur les cibles 1 et 2.

![Plan de requête](./media/database-experimentation-assistant-get-started/dea-get-started-queryplan.png)

Sur n’importe quelle page du rapport d’analyse, sélectionnez le bouton **Imprimer** en haut à droite pour imprimer tout ce qui est visible.

## <a name="next-steps"></a>Étapes suivantes

- Pour savoir comment créer un fichier de trace contenant un journal des événements qui se produisent sur un serveur, consultez [capture trace](database-experimentation-assistant-capture-trace.md).

- Pour une présentation de la DEA et de la démonstration de 19 minutes, regardez la vidéo suivante :

  > [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Introducing-the-Database-Experimentation-Assistant/player]
