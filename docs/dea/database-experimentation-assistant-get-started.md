---
title: Vue d’ensemble du processus de comparaison de charge de travail
description: Assistant Expérimentation de base de données (DEA) est une solution de test A/B permettant de modifier des environnements SQL Server, tels que des mises à niveau ou de nouveaux index.
ms.date: 11/16/2019
ms.prod: sql
ms.prod_service: dea
ms.suite: sql
ms.technology: dea
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: HJToland3
ms.author: jtoland
ms.reviewer: mathoma
ms.custom: seo-lt-2019
ms.openlocfilehash: 18cba7abf0d73197c248a62283d52126873169a3
ms.sourcegitcommit: f018eb3caedabfcde553f9a5fc9c3e381c563f1a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2019
ms.locfileid: "74165751"
---
# <a name="overview-of-the-workload-comparison-process"></a>Vue d’ensemble du processus de comparaison de charge de travail

Assistant Expérimentation de base de données (DEA) vous aide à évaluer la façon dont la charge de travail sur votre serveur source (dans votre environnement actuel) sera exécutée dans votre nouvel environnement. La DEA vous guide tout au long de l’exécution d’un test A/B en effectuant trois étapes :

- Capture d’une trace de charge de travail sur le serveur source.
- Relecture de la trace de la charge de travail capturée sur la cible 1 et la cible 2.
- Analyse des traces de la charge de travail relues collectées à partir de Target 1 et Target 2.

Cet article fournit une vue d’ensemble de ce processus.

## <a name="capturing-a-workload-trace"></a>Capture d’une trace de charge de travail

La première étape du test SQL Server A/B consiste à capturer une trace sur votre serveur source. Le serveur source est généralement le serveur de production. Les fichiers de trace capturent l’intégralité de la charge de travail des requêtes sur ce serveur, y compris les horodateurs.

Éléments à prendre en considération :

- Avant de commencer à capturer votre trace de charge de travail, veillez à sauvegarder les bases de données à partir desquelles vous capturez la trace.
- Un utilisateur de DEA doit être configuré pour se connecter à la base de données à l’aide de l’authentification Windows.
- Un compte de service SQL Server nécessite l’accès au chemin du fichier de trace source.
- Pour la DEA afin de déterminer si les performances d’une requête sont améliorées ou détériorées, cette requête doit s’exécuter au moins 15 fois pendant la période de capture.

## <a name="replaying-a-workload-trace"></a>Relecture d’une trace de charge de travail

La deuxième étape de SQL Server un test A/B consiste à relire le fichier de trace que vous avez capturé sur deux serveurs cibles :

Cible 1, qui imite votre serveur source cible 2, qui imite votre environnement cible proposé.

Les configurations matérielles des cibles 1 et 2 doivent être aussi similaires que possible, de sorte que SQL Server pouvez analyser avec précision l’impact sur les performances de vos modifications proposées.

Éléments à prendre en considération :

- Pour relire une trace de charge de travail, vos ordinateurs doivent être configurés pour s’exécuter Distributed Replay (DReplay) traces.
- Veillez à restaurer les bases de données sur vos serveurs cibles à l’aide de la sauvegarde à partir du serveur source.
- Il est recommandé de redémarrer le service de SQL Server (MSSQLSERVER) dans l’application des services pour améliorer la cohérence dans les résultats de l’évaluation. La mise en cache des requêtes dans SQL Server peut affecter les résultats de l’évaluation.

## <a name="analyzing-the-replayed-workload-traces"></a>Analyse des traces de la charge de travail relue

La dernière étape du processus consiste à générer un rapport d’analyse à l’aide des traces de relecture. Vous pouvez ensuite consulter le rapport d’analyse pour obtenir des informations sur les implications potentielles sur les performances de la modification proposée.

Éléments à prendre en considération :

- Si un ou plusieurs composants sont manquants, une page conditions préalables avec des liens pour les téléchargements s’affiche lorsque vous essayez de générer un nouveau rapport d’analyse (connexion Internet requise).
- Pour afficher un rapport qui a été généré dans une version antérieure de l’outil, vous devez d’abord mettre à jour le schéma.

## <a name="see-also"></a>Voir aussi

- Pour savoir comment générer un fichier de trace avec un journal des événements qui se produisent sur un serveur, consultez [capturer la trace](database-experimentation-assistant-capture-trace.md).
