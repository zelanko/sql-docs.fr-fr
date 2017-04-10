---
title: "R&#233;g&#233;n&#233;rer des proc&#233;dures transactionnelles personnalis&#233;es pour refl&#233;ter des modifications de sch&#233;ma | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "procédures personnalisées [réplication SQL Server]"
  - "réplication transactionnelle, réplication des modifications de schéma"
  - "schémas [réplication SQL Server], réplication des modifications"
ms.assetid: ccf68a13-e748-4455-8168-90e6d2868098
caps.latest.revision: 29
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# R&#233;g&#233;n&#233;rer des proc&#233;dures transactionnelles personnalis&#233;es pour refl&#233;ter des modifications de sch&#233;ma
  Par défaut, la réplication transactionnelle effectue toutes les modifications de données sur l'Abonné via des procédures stockées qui sont générées par des procédures internes pour chaque article de table de la publication. Les trois procédures (une pour les insertions, une pour les mises à jour et une pour les suppressions) sont copiées vers l'Abonné et s'exécutent quand une insertion, une mise à jour ou une suppression est répliquée vers l'Abonné. Quand une modification de schéma est apportée à une table sur un serveur de publication [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], la réplication régénère automatiquement ces procédures en appelant le même ensemble de procédures de script internes, de façon à ce que les nouvelles procédures correspondent au nouveau schéma (la réplication de modifications de schéma n'est pas prise en charge pour les serveurs de publication Oracle).  
  
 Il est également possible de spécifier des procédures personnalisées pour remplacer une ou plusieurs des procédures par défaut. Les procédures personnalisées doivent être modifiées si la modification de schéma affecte la procédure. Par exemple, si une procédure référence une colonne qui est supprimée dans une modification de schéma, les références à la colonne doivent être supprimées de la procédure. Il y a deux façons pour la réplication de propager une nouvelle procédure personnalisée vers les Abonnés :  
  
-   La première option consiste à utiliser une procédure de script personnalisée pour remplacer les procédures par défaut utilisées par la réplication :  
  
    1.  Lors de l’exécution [sp_addarticle & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md), vérifiez le **@schema_option** bit 0 x 02 consiste à **true**.  
  
    2.  Exécutez [sp_register_custom_scripting & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-register-custom-scripting-transact-sql.md) Spécifiez une valeur de 'insert', 'update' ou 'delete' pour le paramètre **@type** et procédure pour le paramètre de script le nom personnalisé **@value**.  
  
     La prochaine fois qu'une modification de schéma est effectuée, la réplication appelle cette procédure stockée pour générer le script de la définition de la nouvelle procédure stockée personnalisée définie par l'utilisateur, puis propage la procédure à chaque Abonné.  
  
-   La deuxième option consiste à utiliser un script qui contient une nouvelle définition de procédure personnalisée :  
  
    1.  Lors de l’exécution [sp_addarticle & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md), définissez le **@schema_option** bit 0 x 02 **false** pour la réplication ne génère pas automatiquement les procédures personnalisées sur l’abonné.  
  
    2.  Avant chaque changement de schéma, créez un fichier de script et inscrivez le script avec la réplication en exécutant [sp_register_custom_scripting & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-register-custom-scripting-transact-sql.md). Spécifiez la valeur 'custom_script' pour le paramètre **@type** et le chemin d’accès au script sur le serveur de publication pour le paramètre **@value**.  
  
     La prochaine fois qu'une modification de schéma pertinente est effectuée, ce script s'exécutera sur chaque Abonné au sein de la même transaction que la commande DDL. Quand la modification de schéma est effectuée, le script est désinscrit. Vous devez réinscrire le script pour qu'il soit exécuté après une modification de schéma ultérieure.  
  
## Voir aussi  
 [Spécifier le mode de propagation des modifications des articles transactionnels](../../../relational-databases/replication/transactional/specify-how-changes-are-propagated-for-transactional-articles.md)   
 [Modifier le schéma dans les bases de données de publication](../../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)  
  
  