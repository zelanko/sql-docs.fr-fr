---
title: Bien démarrer avec l’Assistant expérimentation de base de données pour les mises à niveau de SQL Server
description: Bien démarrer avec l’Assistant expérimentation de base de données
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
manager: jroth
ms.openlocfilehash: 8f5cf6696b66504357279ab45432b4439894e4ca
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66794467"
---
# <a name="get-started-with-database-experimentation-assistant"></a>Bien démarrer avec l’Assistant expérimentation de base de données

L’Assistant base de données expérimentation (DEA) est un test a / B solution pour les modifications dans les environnements SQL Server, telles que les mises à niveau ou de nouveaux index. La DEA vous permet d’évaluer la façon dont la charge de travail sur votre serveur source (dans votre environnement actuel) effectue dans votre nouvel environnement. La DEA vous guide à travers d’en cours d’exécution un A / B test en trois étapes : 

- Capture
- relecture
- Analyse

Cet article vous guide tout au long de ces étapes.

## <a name="capture"></a>Capture

La première étape de SQL Server A / B test consiste à capturer une trace sur votre serveur source. Le serveur source est généralement le serveur de production. Fichiers de trace capturent la charge de travail de requête entière sur ce serveur, y compris les horodateurs. Une version ultérieure, cette trace est relue sur vos serveurs cibles pour l’analyse. Le rapport d’analyse fournit des informations sur la différence de performances de la charge de travail entre vos deux serveurs cibles.

Éléments à prendre en considération :

- Avant de commencer votre capture de trace, veillez à sauvegarder les bases de données à partir duquel vous capturez une trace.
- Un utilisateur DEA doit être configuré pour se connecter à la base de données à l’aide de l’authentification Windows.
- Un compte de service SQL Server requiert l’accès pour le chemin d’accès du fichier de trace source.

Pour capturer une trace sur votre serveur source :

1. Dans la DEA, accédez à **capture toutes les** en sélectionnant l’icône représentant une caméra dans le menu de gauche.

   ![Menu de navigation gauche](./media/database-experimentation-assistant-get-started/dea-get-started-leftnav.png)

1. Entrez ou sélectionnez les informations suivantes :

   - **Nom de la trace**: Le nom de fichier pour le nouveau fichier de trace que vous créez. Éviter un nom de trace qui utilise la convention d’affectation de noms du fichier substitution, par exemple, CaptureName\_NNN.
   - **Durée**: La durée de la capture.
   - **Nom de l’instance SQL Server**: L’instance de SQL Server à partir de laquelle vous souhaitez capturer une trace.
   - **Nom de la base de données**: Le nom de la base de données sur l’ordinateur exécutant SQL Server que vous souhaitez capturer une trace de. Si ce champ est vide, la trace est capturée à partir de toutes les bases de données sur le serveur.
   - **Chemin d’accès pour stocker le fichier de trace source sur la machine SQL Server**: Le chemin d’accès du dossier où vous souhaitez enregistrer le fichier de trace.

1. Assurez-vous que la sauvegarde de la base de données cible. Ensuite, sélectionnez la case à cocher base de données.
1. Sélectionnez **Démarrer** pour démarrer l’enregistrement.

Vous pouvez afficher la progression de votre capture, y compris l’heure de début, la durée et le temps restant. Vous pouvez également démarrer une nouvelle capture pendant que vous attendez que cette capture à la fin. Lorsque votre capture est terminé, utilisez le fichier de sortie pour lancer la deuxième phase : relire le fichier de trace sur vos serveurs cibles.

Pour obtenir des questions courantes sur la capture de trace, consultez le [capturer FAQ](database-experimentation-assistant-capture-trace.md#frequently-asked-questions-about-trace-capture).

## <a name="replay"></a>relecture

La deuxième étape de SQL Server A / B test consiste à relire le fichier de trace qui ont été capturé à vos serveurs cibles. Ensuite, collecter des traces complètes à partir de la relecture pour l’analyse. 

Vous relisez le fichier de trace sur les deux serveurs cibles : une qui imite votre serveur source (cible 1) et l’autre qui reproduit la modification proposée (2 cible). Les configurations matérielles de cible 1 et 2 de la cible doivent être aussi semblables que possible afin de SQL Server peut analyser avec précision l’effet de performances de vos modifications proposées.

Éléments à prendre en considération :

- Pour exécuter la relecture, vos machines doivent être configurés pour exécuter des traces de Distributed Replay (DReplay). Pour plus d’informations, consultez [le programme d’installation Distributed Replay controller et client](https://blogs.msdn.microsoft.com/datamigration/distributed-replay-controller-and-client-setup/).
- Veillez à restaurer les bases de données sur vos serveurs cibles à l’aide de la sauvegarde du serveur source.
- Mise en cache de requête dans SQL Server peut affecter les résultats de l’évaluation. Nous recommandons que vous redémarrez le service SQL Server (MSSQLSERVER) dans l’application de services pour améliorer la cohérence dans les résultats de l’évaluation.

Pour relire le fichier de trace :

1. Dans la DEA, sélectionnez l’icône de lecture dans le menu de gauche pour accéder à **tous les relectures**. La liste des derniers relectures qui s’exécutent pendant la session, si un, apparaît. Pour démarrer une relecture de nouveau, sélectionnez **relire nouvelle**.

1. Entrez ou sélectionnez les informations suivantes :

   - **Nom de la relecture**: Le nom de fichier pour la relecture de trace.
   - **Nom de l’ordinateur contrôleur**: Le nom de l’ordinateur du contrôleur Distributed Replay.
   - **Chemin d’accès au fichier de trace source sur le contrôleur**: Le chemin d’accès de fichier pour le fichier de trace source à partir de [capturer](#capture).
   - **Nom de l’instance SQL Server**: Le nom de l’instance de SQL Server sur laquelle relire la trace de la source.
   - **Chemin d’accès pour stocker le fichier de trace de cible sur l’ordinateur SQL Server**: Le chemin d’accès de dossier pour le fichier de trace de relecture résultant.

1. Sélectionnez la case à cocher pour restaurer la sauvegarde à partir de la première étape.

1. Sélectionnez **Démarrer** pour démarrer la relecture. 

Vous pouvez afficher l’état de votre relecture. Une fois que vous relisez la trace de la source sur les deux de vos serveurs cibles, vous êtes prêt à générer un rapport d’analyse.

Pour les questions courantes sur la relecture, consultez le [relire FAQ](database-experimentation-assistant-replay-trace.md#frequently-asked-questions-about-trace-replay).

## <a name="analysis"></a>Analyse

L’étape finale consiste à générer un rapport d’analyse à l’aide des relire des traces. Le rapport d’analyse peut vous aider à mieux comprendre l’impact sur les performances de la modification proposée.

Éléments à prendre en considération :

- Si un ou plusieurs composants sont manquants, une page de composants requis avec des liens pour les téléchargements s’affiche lorsque vous essayez de générer un rapport d’analyse (connexion internet requise).
- Pour afficher un rapport qui a été généré dans une version antérieure de l’outil, vous devez tout d’abord mettre à jour le schéma.

Pour générer un rapport d’analyse :

1. Dans le menu de gauche, accédez à **rapports d’analyse**. Se connecter à l’ordinateur qui exécute SQL Server où vous stockez vos bases de données de rapport. Une liste de tous les rapports dans le serveur s’affiche. Pour créer un nouveau rapport, sélectionnez **nouveau rapport**.

1. Entrez ou sélectionnez les informations requises pour générer un rapport :

   - **Nom du rapport**: Le nom du rapport d’analyse à créer.
   - **Trace de serveur SQL cible 1**: Le chemin d’accès pour le fichier de trace de relecture sur 1 de la cible.
   - **Trace de serveur SQL cible 2**: Le chemin d’accès pour le fichier de trace de relecture sur le 2 de la cible.

1. Sélectionnez **Démarrer** pour générer le rapport. Le nouveau rapport s’affiche en haut de la liste. L’icône en regard du rapport devient une coche verte quand le rapport a été généré.

À présent, affichez le rapport d’analyse pour obtenir des informations fournies par votre A / B test.

Pour obtenir des questions courantes sur les rapports d’analyse, consultez le [analysis FAQ](database-experimentation-assistant-create-report.md#frequently-asked-questions-about-analysis-reports).

### <a name="analysis-report"></a>Rapport d’analyse

Sur la première page de votre rapport, les informations de version et de build pour les serveurs cibles sur lesquels l’expérience a été exécutée s’affiche. Vous pouvez utiliser le seuil pour ajuster la sensibilité ou la tolérance de panne de votre A / analyse des tests de B. Par défaut, le seuil est défini à 5 %. Toute amélioration des performances qui est supérieur ou égal à 5 % est classée **amélioré**. Sélectionnez les options dans le menu déroulant pour évaluer le rapport à l’aide de seuils de performances différentes.

![Seuil](https://msdnshared.blob.core.windows.net/media/2017/03/threshold.jpg)

Deux graphiques en secteurs présentent les implications en matière de performances de la différence entre deux serveurs cibles pour votre charge de travail. Le graphique de gauche est basé sur le nombre d’exécutions. Le graphique de droite est basé sur des requêtes distinctes. Il existe cinq catégories possibles :

- **Amélioration de**:  Statistiquement, exécution de la requête mieux sur 2 cible que sur 1 de la cible.
- **Détérioré**: Statistiquement, exécution de la requête pire sur 2 cible que sur 1 de la cible.
- **Même**: Il n’existe aucune différence de statistiques pour la requête entre cible 1 et 2 de la cible.
- **Impossible d’évaluer le**: La taille d’échantillon pour la requête est trop petite pour l’analyse statistique. Pour A / B test analysis, DEA nécessite les mêmes requêtes disposer d’au moins 30 exécutions sur chaque cible.
- **Erreur** : La requête erronée au moins une fois sur l’une des cibles.

![Graphique à secteurs](./media/database-experimentation-assistant-get-started/dea-get-started-piechart.png)

Sélectionnez une section pour descendre dans une catégorie particulière et obtenir des métriques de performances, y compris le **Impossible d’évaluer** graphique en secteurs.

La page détaillée pour une performance modifier catégorie affiche une liste de requêtes dans cette catégorie. Le **erreur** page comporte trois onglets :

- **Nouvelles erreurs**: Erreurs qui apparaissaient sur 2 de la cible mais pas sur la cible 1.
- **Erreurs existantes**: Erreurs qui s’est affiché sur la cible 1 et 2 de la cible.
- **Erreurs résolues**: Erreurs qui s’est affiché sur la cible 1 mais pas sur les 2 de la cible.

   ![Page d’erreur](./media/database-experimentation-assistant-get-started/dea-get-started-errorpage.png)

Sélectionnez une requête pour accéder à un **synthèse de la comparaison** page pour cette requête.

Le **comparaison Résumé** page affiche des statistiques de synthèse pour cette requête. Le résumé inclut le nombre d’exécutions, durée moyenne, la moyenne du processeur, moyenne de lectures/écritures et nombre d’erreurs.

![Résumé des statistiques](./media/database-experimentation-assistant-get-started/dea-get-started-summarystats.png)

Si la requête est une erreur, le **des informations d’erreur** onglet affiche plus d’informations sur l’erreur. Le **informations de Plan de requête** onglet affiche des informations sur les plans de requête qui sont utilisés pour la requête sur la cible 1 et 2 de la cible.

![Plan de requête](./media/database-experimentation-assistant-get-started/dea-get-started-queryplan.png)

Sur n’importe quelle page du rapport d’analyse, sélectionnez le **imprimer** bouton dans le coin supérieur droit d’imprimer tout ce qui est visible.

## <a name="next-steps"></a>Étapes suivantes

- Pour savoir comment générer un fichier de trace qui a un journal des événements qui se produisent sur un serveur, consultez [capturer la trace](database-experimentation-assistant-capture-trace.md).

- Pour une présentation 19 minutes DEA et de démonstration, regardez la vidéo suivante :

  > [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Introducing-the-Database-Experimentation-Assistant/player]
