---
title: "Script de journalisation suppl&#233;mentaire Oracle | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5e6ee618-b89b-46c7-92ad-4fc5ef7b777a
caps.latest.revision: 6
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 6
---
# Script de journalisation suppl&#233;mentaire Oracle
  Cette boîte de dialogue affiche le script Oracle de journalisation supplémentaire.  
  
 Lorsque vous préparez une instance de capture de données modifiées pour l'utilisation, le concepteur CDC crée un script Oracle SQL qui configure une journalisation supplémentaire pour les tables à capturer. Le script de journalisation supplémentaire indique à Oracle que lorsqu'une table spécifique est mise à jour, les enregistrements de modification qu'elle écrit dans le journal des transactions doivent contenir les données de toutes les colonnes d'intérêt, et non pas seulement des colonnes qui ont été modifiées.  
  
 Selon les stratégies de l'administrateur de base de données Oracle de votre organisation, l'exécution du script de journalisation supplémentaire peut nécessiter un examen et une approbation par un administrateur de base de données Oracle.  
  
## Options  
 Voici les options disponibles pour l'exécution du script.  
  
 **Exécuter le script**  
 Exécute le script de journalisation supplémentaire sur les tables définies pour l'instance de capture de données modifiées. Pour exécuter ce script, l'utilisateur Oracle doit disposer de l'autorisation ALTER TABLE pour que toutes les tables soient capturées et de l'autorisation SELECT sur la vue DBA_LOG_GROUPS. En outre, l'utilisateur Oracle doit disposer des informations d'identification pour utiliser une base de données Oracle avec les autorisations requises. Vous pouvez laisser le programme vous inviter à entrer les informations d'identification Oracle, puis exécuter le script.  
  
 **Enregistrer sous**  
 Enregistre le script dans un fichier texte. Cette option est utilisée si un administrateur de base de données Oracle (DBA) doit examiner et exécuter le script de journalisation supplémentaire, le programme vous permet d'enregistrer le script dans un fichier texte que vous pouvez ultérieurement envoyer à l'administrateur de base de données Oracle par courrier électronique ou par d'autres moyens en vue de son exécution ultérieure (à l'aide de l'utilitaire SQL*PLUS Oracle ou d'un autre outil pour exécuter des scripts sur une base de données Oracle).  
  
 **Copier**  
 Copie le script dans le Presse-papiers. Lorsque vous serez prêt, vous pourrez coller le script dans n'importe quel emplacement si un administrateur de base de données Oracle (DBA) doit examiner et exécuter le script de journalisation supplémentaire.  
  
## Voir aussi  
 [Procédure : gérer une instance de capture de données modifiées](../../integration-services/change-data-capture/how-to-manage-a-cdc-instance.md)   
 [Gérer une instance de capture de données modifiées](../../integration-services/change-data-capture/manage-a-cdc-instance.md)  
  
  