---
title: Activation de MARS (Multiple Active Result Sets)
description: Décrit comment utiliser MARS avec SQL Server.
ms.date: 09/30/2019
dev_langs:
- csharp
ms.assetid: 576079e4-debe-4ab5-9204-fcbe2ca7a5e2
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: adcedcdfd0c8909d6834c25df8f03a9b5dc2fa5d
ms.sourcegitcommit: 610e49c3e1fa97056611a85e31e06ab30fd866b1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/07/2020
ms.locfileid: "78896961"
---
# <a name="enabling-multiple-active-result-sets"></a>Activation de MARS (Multiple Active Result Sets)

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

MARS (Multiple Active Result Sets) est une fonctionnalité qui opère avec SQL Server pour permettre l’exécution de plusieurs lots sur une seule connexion. Quand MARS est activé pour une utilisation avec SQL Server, chaque objet de commande utilisé ajoute une session à la connexion.  
  
> [!NOTE]
>  Une session MARS unique ouvre une connexion logique que MARS doit utiliser, puis une connexion logique pour chaque commande active.  
  
## <a name="enabling-and-disabling-mars-in-the-connection-string"></a>Activation et désactivation de MARS dans la chaîne de connexion  
  
> [!NOTE]
>  Les chaînes de connexion suivantes utilisent l’exemple de base de données **AdventureWorks** fourni avec SQL Server. Les chaînes de connexion fournies supposent que la base de données est installée sur un serveur nommé MSSQL1. Modifiez la chaîne de connexion en fonction de votre environnement.  
  
La fonctionnalité MARS est désactivée par défaut. Vous pouvez l’activer en ajoutant la paire de mots clés « MultipleActiveResultSets = True » à votre chaîne de connexion. « True » est la seule valeur valide pour l’activation de MARS. L’exemple suivant montre comment se connecter à une instance de SQL Server et spécifier que MARS doit être activé. 
  
```csharp  
string connectionString = "Data Source=MSSQL1;" +   
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" +  
    "MultipleActiveResultSets=True";  
```  
  
Vous pouvez désactiver MARS en ajoutant la paire de mots clés « MultipleActiveResultSets = False » à votre chaîne de connexion. « False » est la seule valeur valide pour la désactivation de MARS. La chaîne de connexion suivante montre comment désactiver MARS.  
  
```csharp  
string connectionString = "Data Source=MSSQL1;" +   
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" +  
    "MultipleActiveResultSets=False";  
```  
  
## <a name="special-considerations-when-using-mars"></a>Considérations spéciales relatives à l’utilisation de MARS  
En général, les applications existantes ne doivent pas être modifiées pour utiliser une connexion prenant en charge MARS. Toutefois, si vous souhaitez utiliser les fonctionnalités MARS dans vos applications, vous devez comprendre les considérations spéciales suivantes.  
  
### <a name="statement-interleaving"></a>Entrelacement d’instructions  
Les opérations MARS s’exécutent de façon synchrone sur le serveur. L’entrelacement des instructions SELECT et BULK INSERT est autorisé. Toutefois, les instructions DML (Data Manipulation Language) et DDL (Data Definition Language) s’exécutent de manière atomique. Toutes les instructions tentant de s’exécuter pendant l’exécution d’un lot atomique sont bloquées. L’exécution en parallèle au niveau du serveur n’est pas une fonctionnalité MARS.  
  
Si deux lots sont soumis sous une connexion MARS, l’un d’eux contenant une instruction SELECT, l’autre contenant une instruction DML, l’instruction DML peut commencer l’exécution dans le cadre de l’exécution de l’instruction SELECT. Toutefois, l’instruction DML doit s’exécuter jusqu’à la fin pour que l’instruction SELECT puisse progresser. Si les deux instructions s’exécutent sous la même transaction, toute modification apportée par une instruction DML après le début de l’exécution de l’instruction SELECT n’est pas visible pour l’opération de lecture.  
  
Une instruction WAITFOR à l’intérieur d’une instruction SELECT ne génère pas la transaction pendant qu’elle est en attente, c’est-à-dire, jusqu’à ce que la première ligne soit produite. Cela implique qu’aucun autre lot ne peut s’exécuter dans la même connexion pendant qu’une instruction WAITFOR est en attente.  
  
### <a name="mars-session-cache"></a>Cache de session MARS  
Lorsqu’une connexion est ouverte avec MARS activée, une session logique est créée, ce qui ajoute une surcharge supplémentaire. Afin de minimiser la charge et d’améliorer les performances, **SqlClient** met en cache la session MARS à l’intérieur d’une connexion. Le cache contient au plus 10 sessions MARS. Cette valeur n'est pas ajustable par l'utilisateur. Si la limite de session est atteinte, une nouvelle session est créée, aucune erreur n’est générée. Le cache et les sessions qu’il contient sont partagées par connexion ; elles ne sont pas partagées entre les connexions. Lorsqu’une session est mise en production, elle est retournée au pool, à moins que la limite supérieure du pool ne soit atteinte. Si le pool de caches est plein, la session est fermée. Les sessions MARS n’expirent pas. Elles sont nettoyées uniquement lorsque l’objet de connexion est supprimé. Le cache de session MARS n’est pas préchargé. Il est chargé, car l’application requiert plus de sessions.  
  
### <a name="thread-safety"></a>Sécurité des threads  
Les opérations MARS ne sont pas thread-safe.  
  
### <a name="connection-pooling"></a>Regroupement de connexions  
Les connexions compatibles MARS sont regroupées par pool comme n’importe quelle autre connexion. Si une application ouvre deux connexions, l’une avec MARS activée et l’autre avec MARS désactivée, les deux connexions se trouvent dans des pools distincts.
  
### <a name="sql-server-batch-execution-environment"></a>Environnement d'exécution par lot SQL Server  
Lorsqu’une connexion est ouverte, un environnement par défaut est défini. Cet environnement est ensuite copié dans une session MARS logique.  
  
L’environnement d’exécution par lot comprend les composants suivants :  
  
- Définir les options (par exemple, ANSI_NULLS, DATE_FORMAT, LANGUAGE, TEXTSIZE)  
  
- Contexte de sécurité (rôle d’utilisateur/d’application)  
  
- Contexte de la base de données (base de données actuelle)  
  
- Variables d’état d’exécution (par exemple, @@ERROR, @@ROWCOUNT, @@FETCH_STATUS @@IDENTITY)  
  
- Tables temporaires de niveau supérieur  
  
Avec MARS, un environnement d’exécution par défaut est associé à une connexion. Chaque nouveau traitement dont l’exécution commence sous une connexion donnée reçoit une copie de l’environnement par défaut. Chaque fois que le code est exécuté sous un lot donné, toutes les modifications apportées à l’environnement sont étendues au lot spécifique. Une fois l’exécution achevée, les paramètres d’exécution sont copiés dans l’environnement par défaut. Dans le cas où un lot unique émet plusieurs commandes à exécuter de façon séquentielle sous la même transaction, les sémantiques sont les mêmes que celles exposées par les connexions impliquant des clients ou des serveurs dans les versions précédentes.  
  
### <a name="parallel-execution"></a>Exécution parallèle  
MARS n’est pas conçu pour supprimer toutes les exigences de connexions multiples dans une application. Si une application a besoin d’une véritable exécution parallèle des commandes sur un serveur, vous devez utiliser plusieurs connexions.  
  
Par exemple, considérez le scénario suivant. Deux objets de commande sont créés, l’un pour le traitement d’un jeu de résultats et l’autre pour la mise à jour des données ; ils partagent une connexion commune via MARS. Dans ce scénario, `Transaction`.`Commit` échoue lors de la mise à jour jusqu’à ce que tous les résultats aient été lus sur le premier objet de commande, en générant l’exception suivante :  
  
Message : Le contexte de transaction est utilisé par une autre session.  
  
Source : Fournisseur de données Microsoft SqlClient  
  
Attendu : (Null)  
  
Reçu : Microsoft.Data.SqlClient.SqlException  
  
Trois options permettent de prendre en charge ce scénario :  
  
- Démarrez la transaction après la création du lecteur, afin qu’il ne fasse pas partie de la transaction. Chaque mise à jour devient alors sa propre transaction.  
  
- Validez tout le travail une fois le lecteur fermé. Cela peut entraîner un lot important de mises à jour.  
  
- N’utilisez pas MARS ; utilisez plutôt une connexion distincte pour chaque objet de commande comme avant MARS.  
  
### <a name="detecting-mars-support"></a>Détection de la prise en charge de MARS  
Une application peut vérifier la prise en charge de MARS en lisant la valeur `SqlConnection.ServerVersion`. Le nombre majeur doit être 9 pour SQL Server 2005 et 10 pour SQL Server 2008.  
  
## <a name="next-steps"></a>Étapes suivantes
- [MARS (Multiple Active Result Sets)](multiple-active-result-sets-mars.md)
