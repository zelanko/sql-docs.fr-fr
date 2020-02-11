---
title: Regénérer des procédures transactionnelles personnalisées pour refléter des modifications de schéma | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- custom procedures [SQL Server replication]
- transactional replication, replicating schema changes
- schemas [SQL Server replication], replicating changes
ms.assetid: ccf68a13-e748-4455-8168-90e6d2868098
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8a99a98fd0d471e8cb0f8ab880ae1a6c55e1b121
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62655504"
---
# <a name="regenerate-custom-transactional-procedures-to-reflect-schema-changes"></a>Régénérer des procédures transactionnelles personnalisées pour refléter des modifications de schéma
  Par défaut, la réplication transactionnelle effectue toutes les modifications de données sur l'Abonné via des procédures stockées qui sont générées par des procédures internes pour chaque article de table de la publication. Les trois procédures (une pour les insertions, une pour les mises à jour et une pour les suppressions) sont copiées vers l'Abonné et s'exécutent quand une insertion, une mise à jour ou une suppression est répliquée vers l'Abonné. Quand une modification de schéma est apportée à une table sur un serveur de publication [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , la réplication régénère automatiquement ces procédures en appelant le même ensemble de procédures de script internes, de façon à ce que les nouvelles procédures correspondent au nouveau schéma (la réplication de modifications de schéma n'est pas prise en charge pour les serveurs de publication Oracle).  
  
 Il est également possible de spécifier des procédures personnalisées pour remplacer une ou plusieurs des procédures par défaut. Les procédures personnalisées doivent être modifiées si la modification de schéma affecte la procédure. Par exemple, si une procédure référence une colonne qui est supprimée dans une modification de schéma, les références à la colonne doivent être supprimées de la procédure. Il y a deux façons pour la réplication de propager une nouvelle procédure personnalisée vers les Abonnés :  
  
-   La première option consiste à utiliser une procédure de script personnalisée pour remplacer les procédures par défaut utilisées par la réplication :  
  
    1.  Lors de l’exécution de [sp_addarticle &#40;&#41;Transact-SQL ](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql), **@schema_option** Assurez-vous que le bit 0x02 a la **valeur true**.  
  
    2.  Exécutez [sp_register_custom_scripting &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-register-custom-scripting-transact-sql) et spécifiez la valeur’Insert', 'Update’ou’Delete’pour le paramètre **@type** et le nom de la procédure de script personnalisée pour le paramètre. **@value**  
  
     La prochaine fois qu'une modification de schéma est effectuée, la réplication appelle cette procédure stockée pour générer le script de la définition de la nouvelle procédure stockée personnalisée définie par l'utilisateur, puis propage la procédure à chaque Abonné.  
  
-   La deuxième option consiste à utiliser un script qui contient une nouvelle définition de procédure personnalisée :  
  
    1.  Lors de l’exécution de [sp_addarticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql), **@schema_option** affectez la valeur **false** au bit 0x02 afin que la réplication ne génère pas automatiquement de procédures personnalisées sur l’abonné.  
  
    2.  Avant chaque modification de schéma, créez un nouveau fichier de script et inscrivez le script avec la réplication en exécutant [sp_register_custom_scripting &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-register-custom-scripting-transact-sql). Spécifiez la valeur « custom_script » pour le paramètre **@type** et le chemin d’accès au script sur le serveur de publication **@value**pour le paramètre.  
  
     La prochaine fois qu'une modification de schéma pertinente est effectuée, ce script s'exécutera sur chaque Abonné au sein de la même transaction que la commande DDL. Quand la modification de schéma est effectuée, le script est désinscrit. Vous devez réinscrire le script pour qu'il soit exécuté après une modification de schéma ultérieure.  
  
## <a name="see-also"></a>Voir aussi  
 [Spécifier le mode de propagation des modifications des articles transactionnels](transactional-articles-specify-how-changes-are-propagated.md)   
 [Modifier le schéma dans les bases de données de publication](../publish/make-schema-changes-on-publication-databases.md)  
  
  
