---
title: Always Encrypted avec enclaves sécurisées
description: Découvrez la fonctionnalité Always Encrypted avec enclaves sécurisées pour SQL Server.
ms.custom: seo-lt-2019
ms.date: 10/31/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
author: jaszymas
ms.author: jaszymas
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 3ad3743b35570ddb0f4644b909ca06339444143e
ms.sourcegitcommit: 620a868e623134ad6ced6728ce9d03d7d0038fe0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87410935"
---
# <a name="always-encrypted-with-secure-enclaves"></a>Always Encrypted avec enclaves sécurisées
[!INCLUDE [sqlserver2019-windows-only](../../../includes/applies-to-version/sqlserver2019-windows-only.md)]
 
Always Encrypted avec enclaves sécurisées fournit des fonctionnalités supplémentaires à la fonction [Always Encrypted](always-encrypted-database-engine.md).

Introduit dans SQL Server 2016, Always Encrypted protège la confidentialité des données sensibles contre les programmes malveillants et les utilisateurs *non autorisés* à privilèges élevés de SQL Server. Les utilisateurs non autorisés à privilèges élevés sont les administrateurs de bases de données (DBA), les administrateurs d’ordinateurs, les administrateurs de cloud ou toute autre personne qui a un accès légitime aux instances de serveur, au matériel, etc., mais ne devant pas avoir accès à tout ou partie des données réelles.  

Sans les améliorations abordées dans cet article, Always Encrypted protège les données en les chiffrant côté client, et en n’autorisant jamais l’affichage en texte clair des données ou des clés de chiffrement correspondantes dans le moteur SQL Server. Par conséquent, la fonctionnalité sur les colonnes chiffrées à l’intérieur de la base de données est extrêmement limitée. Les seules opérations que SQL Server peut effectuer sur les données chiffrées sont les comparaisons d’égalité (disponibles seulement avec le chiffrement déterministe). Toutes les autres opérations, notamment les opérations de chiffrement (chiffrement de données initial ou rotation de clés) et/ou les calculs complexes (par exemple, les critères spéciaux), ne sont pas prises en charge à l’intérieur de la base de données. Les utilisateurs doivent déplacer les données hors de la base de données pour effectuer ces opérations côté client.

Always Encrypted *avec enclaves sécurisées* résout ces limitations en autorisant les calculs sur les données de texte en clair à l’intérieur d’une enclave sécurisée côté serveur. Une enclave sécurisée est une région de mémoire protégée dans le processus SQL Server qui agit comme un environnement d’exécution approuvé pour le traitement des données sensibles dans le moteur SQL Server. Une enclave sécurisée apparaît sous la forme d’une boîte noire pour le reste de SQL Server et des autres processus sur l’ordinateur d’hébergement. Il n’existe aucun moyen d’afficher les données ou le code à l’intérieur de l’enclave depuis l’extérieur, même avec un débogueur.  


Always Encrypted utilise des enclaves sécurisées, comme illustré dans le diagramme suivant :

![flux de données](./media/always-encrypted-enclaves/ae-data-flow.png)



Lors de l’analyse de la requête d’une application, le moteur SQL Server détermine si la requête contient des opérations sur les données chiffrées qui nécessitent l’utilisation de l’enclave sécurisée. Pour les requêtes où l’enclave sécurisée doit être accessible :

- Le pilote client envoie les clés de chiffrement de colonne requises pour les opérations à l’enclave sécurisée (via un canal sécurisé). 
- Ensuite, le pilote client soumet la requête pour exécution, ainsi que les paramètres de la requête chiffrée.

Pendant le traitement de la requête, les données ou les clés de chiffrement de colonne ne sont pas exposées en texte clair dans le moteur SQL Server en dehors de l’enclave sécurisée. Le moteur SQL Server délègue les opérations de chiffrement et les calculs sur les colonnes chiffrées à l’enclave sécurisée. Si nécessaire, l’enclave sécurisée déchiffre les paramètres de la requête et/ou les données stockées dans les colonnes chiffrées et effectue les opérations demandées.

Dans [!INCLUDE[sql-server-2019](../../../includes/sssqlv15-md.md)], Always Encrypted avec enclaves sécurisées utilise des enclaves mémoire sécurisées de [sécurité basée sur la virtualisation (VBS)](https://www.microsoft.com/security/blog/2018/06/05/virtualization-based-security-vbs-memory-enclaves-data-protection-through-isolation/), également appelées mode sécurisé virtuel ou enclaves VSM, dans Windows.

## <a name="why-use-always-encrypted-with-secure-enclaves"></a>Pourquoi utiliser Always Encrypted avec enclaves sécurisées ?

Avec les enclaves sécurisées, Always Encrypted protège la confidentialité des données sensibles, tout en offrant les avantages suivants :

- **Chiffrement sur place** : les opérations de chiffrement des données sensibles (par exemple, le chiffrement des données initiales ou la permutation d’une clé de chiffrement de colonne) sont effectuées à l’intérieur de l’enclave sécurisée et ne nécessitent pas le déplacement des données en dehors de la base de données. Vous pouvez émettre le chiffrement sur place à l’aide de l’instruction Transact-SQL ALTER TABLE, et vous n’avez pas besoin d’utiliser des outils, comme l’Assistant Always Encrypted dans SSMS ou la cmdlet PowerShell Set-SqlColumnEncryption.

- **Calculs riches** : les opérations sur des colonnes chiffrées, notamment les critères spéciaux (prédicat LIKE) et les comparaisons de plages, sont prises en charge à l’intérieur de l’enclave sécurisée, ce qui rend Always Encrypted accessible à une large gamme d’applications et de scénarios qui requièrent que ces calculs s’effectuent dans le système de base de données.

## <a name="secure-enclave-attestation"></a>Attestation d’enclave sécurisée

L’enclave sécurisée à l’intérieur du moteur SQL Server peut accéder aux données sensibles stockées dans les colonnes de base de données chiffrées et les clés de chiffrement de colonne correspondantes en texte en clair. Avant de soumettre une requête qui implique des calculs d’enclave à SQL Server, le pilote client à l’intérieur de l’application doit vérifier que l’enclave sécurisée est une enclave authentique basée sur une technologie donnée (par exemple, VBS) et que le code s’exécutant à l’intérieur de l’enclave a été signé pour s’exécuter à l’intérieur de l’enclave. 

Le processus de vérification de l’enclave est appelé **attestation d’enclave** et implique généralement un pilote client au sein de l’application, et une communication entre SQL Server et un service d’attestation externe. Les détails du processus d’attestation dépendent de la technologie de l’enclave et du service d’attestation.

Le processus d’attestation pris en charge par SQL Server pour les enclaves sécurisées VBS dans [!INCLUDE[sql-server-2019](../../../includes/sssqlv15-md.md)] est l’attestation de runtime Windows Defender System Guard, qui utilise le service HGS (Host Guardian Service) comme service d’attestation. Vous devez configurer SGH dans votre environnement et inscrire l’ordinateur qui héberge votre instance SQL Server dans SGH. Vous devez également configurer vos outils ou applications client (par exemple, SQL Server Management Studio) avec une attestation SGH.

## <a name="supported-client-drivers"></a>Pilotes clients pris en charge

Pour utiliser Always Encrypted avec enclaves sécurisées, une application doit utiliser un pilote client qui prend en charge la fonctionnalité. Vous devez configurer l’application et le pilote client pour autoriser les calculs d’enclave et l’attestation d’enclave. Pour plus d’informations, notamment la liste des pilotes clients pris en charge, consultez [Always Encrypted avec enclaves sécurisées](always-encrypted-enclaves.md).

## <a name="enclave-enabled-keys"></a>Clés prenant en charge l’enclave

Always Encrypted avec enclaves sécurisées introduit le concept des clés prenant en charge l’enclave :

- **Clé principale de colonne prenant en charge l’enclave** : clé principale de colonne qui possède la propriété ENCLAVE_COMPUTATIONS spécifiée dans l’objet de métadonnées de la clé principale de colonne à l’intérieur de la base de données. L’objet de métadonnées de la clé principale de colonne doit également contenir une signature valide des propriétés des métadonnées.
- **Clé de chiffrement de colonne prenant en charge l’enclave** : clé de chiffrement de colonne qui est chiffrée avec une clé principale de colonne prenant en charge l’enclave.

Lorsque le moteur SQL Server détermine les opérations, spécifiées dans une requête, qui doivent être effectuées à l’intérieur de l’enclave sécurisée, le moteur SQL Server demande que le pilote client partage les clés de chiffrement de colonne qui sont nécessaires pour les calculs avec l’enclave sécurisée. Le pilote client partage les clés de chiffrement de colonne uniquement si les clés prennent en charge l’enclave (c’est-à-dire qu’elles sont chiffrées avec des clés principales de colonne prenant en charge l’enclave) et qu’elles sont correctement signées. Sinon, la requête échoue.

Pour plus d’informations, consultez [Gérer des clés pour Always Encrypted avec enclaves sécurisées](always-encrypted-enclaves-manage-keys.md).

## <a name="enclave-enabled-columns"></a>Colonnes prenant en charge l’enclave

Une colonne prenant en charge l’enclave est une colonne de base de données qui est chiffrée avec une clé de chiffrement de colonne prenant en charge l’enclave. La fonctionnalité disponible pour une colonne prenant en charge l’enclave varie selon le type de chiffrement que la colonne utilise.

- **Chiffrement déterministe** : les colonnes prenant en charge l’enclave utilisant le chiffrement déterministe prennent en charge le chiffrement sur place, mais aucune autre opération à l’intérieur de l’enclave sécurisée. La comparaison d’égalité est prise en charge, mais effectuée en comparant le texte chiffré en dehors de l’enclave.  
- **Chiffrement aléatoire** : les colonnes prenant en charge l’enclave utilisant le chiffrement aléatoire prennent en charge le chiffrement sur place, ainsi que les calculs riches à l’intérieur de l’enclave sécurisée. Les calculs riches pris en charge sont les critères spéciaux et les [opérateurs de comparaison](../../../t-sql/language-elements/comparison-operators-transact-sql.md), notamment la comparaison d’égalité.

Pour plus d’informations sur les types de chiffrement, consultez [Chiffrement Always Encrypted](always-encrypted-cryptography.md).

Le tableau suivant récapitule les fonctionnalités disponibles pour les colonnes chiffrées, selon que les colonnes utilisent des clés de chiffrement de colonne prenant en charge l’enclave et un type de chiffrement.

| **opération**| **La colonne ne prend PAS en charge l’enclave** |**La colonne ne prend PAS en charge l’enclave**| **La colonne prend en charge l’enclave**  |**La colonne prend en charge l’enclave** |
|:---|:---|:---|:---|:---|
| | **Chiffrement aléatoire**  | **Chiffrement déterministe**     | **Chiffrement aléatoire**      | **Chiffrement déterministe**     |
| **Chiffrement sur place** | Non pris en charge  | Non pris en charge   | Prise en charge         | Prise en charge    |
| **Comparaison d’égalité**   | Non pris en charge | Pris en charge en dehors de l’enclave | Pris en charge (à l’intérieur de l’enclave) | Pris en charge en dehors de l’enclave |
| **Opérateurs de comparaison au-delà de l’égalité** | Non pris en charge  | Non pris en charge   | Prise en charge      | Non pris en charge     |
| **LIKE**    | Non pris en charge      | Non pris en charge    | Prise en charge     | Non pris en charge    |

Le chiffrement sur place inclut la prise en charge des opérations suivantes à l’intérieur de l’enclave :

- Chiffrement initial des données stockées dans une colonne existante.
- Nouveau chiffrement des données existantes dans une colonne, par exemple :
  
  - Permutation de la clé de chiffrement de colonne (nouveau chiffrement la colonne avec une nouvelle clé).
  - Modification du type de chiffrement.  

- Déchiffrement des données stockées dans une colonne chiffrée (conversion de la colonne en une colonne de texte en clair).

Pour que le chiffrement sur place soit possible, la clé (ou les clés) de chiffrement de colonne impliquée dans les opérations de chiffrement, doit prendre en charge l’enclave :

- Chiffrement initial : la clé de chiffrement de colonne pour la colonne en cours de chiffrement doit prendre en charge l’enclave.
- Nouveau chiffrement : la clé de chiffrement de colonne actuelle et cible (si différente de la clé actuelle) doivent prendre en charge l’enclave.
- Déchiffrement : la clé de chiffrement de colonne actuelle de la colonne doit prendre en charge l’enclave.

### <a name="indexes-on-enclave-enabled-columns-using-randomized-encryption"></a>Index sur des colonnes prenant en charge les enclaves à l’aide d’un chiffrement aléatoire
Vous pouvez créer des index non cluster sur des colonnes prenant en charge les enclaves à l’aide d’un chiffrement aléatoire pour accélérer l’exécution de requêtes enrichies. Pour garantir qu’un index sur une colonne chiffrée à l’aide d’un chiffrement aléatoire n’entraîne pas la fuite de données sensibles tout en étant utile pour le traitement des requêtes au sein de l’enclave, les valeurs de clés dans la structure des données d’index (B-tree) sont chiffrées et triées en fonction de leur valeurs de texte en clair. Lorsque l’exécuteur de requête dans le moteur SQL Server utilise un index sur une colonne chiffrée pour effectuer des calculs au sein d’une enclave, il parcourt l’index pour rechercher des valeurs spécifiques stockées dans la colonne. Chaque recherche peut impliquer plusieurs comparaisons. L’exécuteur de requête délègue chaque comparaison à l’enclave, qui déchiffre une valeur stockée dans la colonne et la valeur de clé de l’index chiffré à comparer, il effectue la comparaison sur du texte en clair et retourne le résultat de la comparaison à l’exécuteur. 

La création d’index sur des colonnes qui utilisent le chiffrement aléatoire et ne prennent pas en charge les enclaves n’est toujours pas prise en charge.

Pour plus d’informations, consultez [Créer et utiliser des index sur des colonnes à l’aide d’Always Encrypted avec enclaves sécurisées](always-encrypted-enclaves-create-use-indexes.md). Pour des informations générales, non spécifiques à Always Encrypted, sur la façon dont fonctionne l’indexation dans SQL Server, consultez [Description des index en cluster non cluster](../../indexes/clustered-and-nonclustered-indexes-described.md).

#### <a name="database-recovery"></a>Récupération de base de données

Si une instance de SQL Server échoue, ses bases de données peuvent être laissées dans un état où les fichiers de données peuvent contenir des modifications résultant de transactions incomplètes. Lorsque l’instance est démarrée, elle exécute un processus appelé [récupération de base de données](../../logs/the-transaction-log-sql-server.md#recovery-of-all-incomplete-transactions-when--is-started), qui implique la restauration de chaque transaction incomplète trouvée dans le journal des transactions pour garantir que l’intégrité de la base de données est préservée. Si une transaction incomplète a apporté des modifications à un index, ces modifications doivent également être annulées. Par exemple, certaines valeurs de clés dans l’index peuvent devoir être supprimées ou réinsérées.

> [!IMPORTANT]
> Microsoft recommande fortement d'activer la [Récupération de base de données accélérée (ADR)](../../backup-restore/restore-and-recovery-overview-sql-server.md#adr) pour votre base de données **avant** de créer le premier index sur une colonne prenant en charge les enclaves avec un chiffrement aléatoire.

Avec le [processus de récupération de base de données traditionnel](https://docs.microsoft.com/azure/sql-database/sql-database-accelerated-database-recovery#the-current-database-recovery-process) (qui suit le modèle de récupération [ARIES](https://people.eecs.berkeley.edu/~brewer/cs262/Aries.pdf)), pour annuler une modification apportée à un index, SQL Server doit attendre qu’une application fournisse la clé de chiffrement de colonne pour la colonne de l’enclave, ce qui peut prendre un certain temps. L’ADR réduit notablement le nombre d’opérations d’annulation qui doivent être reportées parce qu’une clé de chiffrement de colonne n’est pas disponible dans le cache au sein de l’enclave. Par conséquent, elle augmente sensiblement la disponibilité de la base de données en réduisant au minimum le risque de blocage d’une nouvelle transaction. Avec ADR activée, SQL Server peut toujours avoir besoin d’une clé de chiffrement de colonne pour effectuer le nettoyage d’anciennes versions de données. Cependant, cette tâche d’arrière-plan n’affecte pas la disponibilité des transactions de la base de données ou des utilisateurs. Toutefois, vous pouvez voir les messages d’erreur dans le journal des erreurs, qui indiquent des opérations de nettoyage ayant échoué parce qu’il manquait une clé de chiffrement de colonne.

### <a name="indexes-on-enclave-enabled-columns-using-deterministic-encryption"></a>Index sur des colonnes prenant en charge les enclaves à l’aide d’un chiffrement déterministe

Un index sur une colonne utilisant un chiffrement déterministe est trié en fonction du texte chiffré (pas du texte en clair), que la colonne prenne ou non en charge les enclaves.

## <a name="security-considerations"></a>Considérations relatives à la sécurité

Les considérations de sécurité suivantes s’appliquent à Always Encrypted avec enclaves sécurisés.

- La sécurité de vos données au sein de l’enclave dépend d’un protocole et d’un service d’attestation. Par conséquent, vous devrez vérifier que le service et les stratégies d’attestation mis en œuvre par le service d’attestation sont bien gérés par un administrateur approuvé. De plus, les services d’attestation prennent généralement en charge des stratégies et des protocoles d’attestation différents, dont certains procèdent à une vérification minimale de l’enclave et de son environnement et sont conçus pour les tests et le développement. Respectez scrupuleusement les instructions spécifiques à votre service d’attestation pour vérifier que vous utilisez les configurations et les stratégies recommandées pour vos déploiements de production. 
- Le chiffrement d’une colonne à l’aide d’un chiffrement aléatoire avec une clé CEK prenant en charge les enclaves peut entraîner une fuite de l’ordre des données stockées dans la colonne, puisque ces colonnes prennent en charge des comparaisons de plages. Par exemple, si une colonne chiffrée contenant les salaires des employés a un index, un administrateur de base de données malveillant pourrait analyser l’index pour trouver la valeur de salaire chiffrée maximale et identifier une personne touchant le salaire maximal (en supposant que le nom de la personne n’est pas chiffré). 
- Si vous utilisez Always Encrypted pour protéger des données sensibles contre un accès non autorisé des administrateurs de bases de données, ne partagez pas les clés principales des colonnes ou les clés de chiffrement des colonnes avec les administrateurs de bases de données. Un administrateur de base de données peut gérer des index sans avoir directement accès aux clés, en tirant parti du cache des clés de chiffrement de colonne au sein de l’enclave.

## <a name="considerations-for-availability-groups-and-database-migration"></a><a name="anchorname-1-considerations-availability-groups-db-migration"></a> Considérations relatives aux groupes de disponibilité et à la migration de base de données

Quand vous configurez un groupe de disponibilité Always On requis pour prendre en charge des requêtes à l’aide d’enclaves, vous devez vous assurer que toutes les instances de SQL Server qui hébergent les bases de données dans le groupe de disponibilité prennent en charge Always Encrypted avec des enclaves sécurisées et ont une enclave configurée. Si la base de données principale prend en charge les enclaves, mais que ce n’est pas le cas d’un réplica secondaire, toute requête qui tente d’utiliser la fonctionnalité d’Always Encrypted avec des enclaves sécurisés échoue.

Lorsque vous restaurez un fichier de sauvegarde d’une base de données qui utilise la fonctionnalité d’Always Encrypted avec des enclaves sécurisées sur une instance de SQL Server qui n’a pas d’enclave configurée, l’opération de restauration réussit et toutes les fonctionnalités qui ne reposent pas sur l’enclave sont disponibles. Toutefois, toutes les requêtes suivantes utilisant la fonctionnalité de l’enclave échouent, et les index sur des colonnes prenant en charge des enclaves à l’aide d’un chiffrement aléatoire ne sont plus valides. La même chose est valable lorsque vous joignez une base de données utilisant Always Encrypted avec des enclaves sécurisées sur l’instance pour laquelle l’enclave n’est pas configurée.

Si votre base de données contient des index sur des colonnes prenant en charge les enclaves utilisant un chiffrage aléatoire, veillez à activer [Récupération de base de données accélérée (ADR)](../../backup-restore/restore-and-recovery-overview-sql-server.md#adr) dans la base de données avant de créer une sauvegarde de base de données. ADR garantit que la base de données, notamment les index, est disponible immédiatement après la restauration de la base de données. Pour plus d’informations, consultez [Récupération de la base de données](#database-recovery).

Lorsque vous migrez votre base de données à l’aide d’un fichier bacpac, vous devez vous assurer que vous supprimez toutes les colonnes des index prenant en charge les enclaves à l’aide d’un chiffrement aléatoire avant de créer le fichier bacpac.

## <a name="known-limitations"></a>Limites connues
Always Encrypted avec enclaves sécurisées résout certaines limitations d’Always Encrypted en autorisant les opérations suivantes :

- Opérations de chiffrement sur place.
- Critères spéciaux (LIKE) et les opérateurs de comparaison sur la colonne chiffrée à l’aide d’un chiffrement aléatoire.
    > [!NOTE]
    > Les opérations ci-dessus sont prises en charge pour les colonnes de chaînes de caractères qui utilisent des classements avec un ordre de tri binary2 (classements BIN2). Les colonnes de chaînes de caractères utilisant des classements autres que BIN2 peuvent être chiffrées avec un chiffrement aléatoire et des clés de chiffrement de colonne prenant en charge les enclaves. Toutefois, la seule fonctionnalité nouvelle activée pour ces colonnes est le chiffrement sur place.
- Création d’index non cluster et de statistiques sur les colonnes en utilisant un chiffrement aléatoire.

Toutes les autres limitations d’Always Encrypted listées dans [Détails de la fonctionnalité](always-encrypted-database-engine.md#feature-details) s’appliquent également à Always Encrypted avec enclaves sécurisées.

Les limitations suivantes sont spécifiques à Always Encrypted avec enclaves sécurisées :

- Il est impossible de créer des index cluster sur des colonnes prenant en charge les enclaves à l’aide d’un chiffrement aléatoire.
- Les colonnes prenant en charge les enclaves utilisant un chiffrement aléatoire ne peuvent pas être des colonnes de clé primaire, ni être référencées par des contraintes de clé étrangères ou des contraintes de clé unique.
- Seules les jointures de boucles imbriquées (avec des index, le cas échéant) sont prises en charge sur les colonnes avec enclave utilisant un chiffrement aléatoire. Les jointures de hachage et de fusion ne sont pas prises en charge. 
- Les opérations de chiffrement sur place ne peuvent pas être combinées avec d’autres modifications des métadonnées de la colonne, à l’exception des modifications d’un classement au sein de la même page de codes et possibilité de valeur null. Par exemple, vous ne pouvez pas chiffrer, rechiffrer ou déchiffrer une colonne ET changer un type de données de la colonne dans une seule instruction Transact-SQL `ALTER TABLE`/`ALTER COLUMN`. Utilisez deux instructions distinctes.
- L’utilisation de clés prenant en charge les enclaves pour les colonnes dans des tables en mémoire n’est pas prise en charge.
- Les expressions qui définissent des colonnes calculées ne peuvent pas effectuer de calculs sur des colonnes avec enclave utilisant un chiffrement aléatoire (même si les calculs sont basés sur des comparaisons Like ou Range).
- Les caractères d’échappement ne sont pas pris en charge dans les paramètres de l’opérateur LIKE sur les colonnes avec enclave utilisant un chiffrement aléatoire.
- Les requêtes avec l’opérateur LIKE ou un opérateur de comparaison avec un paramètre de requête utilisant l’un des types de données suivants (qui deviennent des objets volumineux après chiffrement) ignorent les index et effectuent des analyses de table.
    - `nchar[n]` et `nvarchar[n]`, si n est supérieur à 3967.
    - `char[n]`, `varchar[n]`, `binary[n]`, `varbinary[n]`, si n est supérieur à 7935.
- Limitations des outils :
  - Les seuls magasins de clés pris en charge pour le stockage des clés principales de colonne prenant en charge l’enclave sont le Magasin de certificats Windows et Azure Key Vault.
  - L’importation/exportation de bases de données contenant des clés activées pour les enclaves n’est pas prise en charge.
  - Pour déclencher une opération de chiffrement sur place via `ALTER TABLE`/`ALTER COLUMN`, vous devez émettre l’instruction à l’aide d’une fenêtre de requête dans SSMS ou vous pouvez écrire votre propre programme qui émet l’instruction. Actuellement, l’applet de commande Set-SqlColumnEncryption dans le module PowerShell SqlServer et l’Assistant Always Encrypted dans SQL Server Management Studio ne prennent pas en charge le chiffrement sur place : ils déplacent les données en dehors de la base de données pour les opérations de chiffrement, même si les clés de chiffrement de colonne utilisées pour les opérations prennent en charge l’enclave.

## <a name="next-steps"></a>Étapes suivantes
- [Tutoriel : Bien démarrer avec Always Encrypted avec enclaves sécurisées en utilisant SSMS](../tutorial-getting-started-with-always-encrypted-enclaves.md)
- [Configurer et utiliser Always Encrypted avec enclaves sécurisées](configure-always-encrypted-enclaves.md)

## <a name="see-also"></a>Voir aussi
- [Gérer des clés pour Always Encrypted avec enclaves sécurisées](always-encrypted-enclaves-manage-keys.md)
- [Configurer le chiffrement de colonne sur place en utilisant Always Encrypted avec enclaves sécurisées](always-encrypted-enclaves-configure-encryption.md)
- [Interroger des colonnes en utilisant Always Encrypted avec enclaves sécurisées](always-encrypted-enclaves-query-columns.md)
- [Activer Always Encrypted avec enclaves sécurisées pour les colonnes chiffrées existantes](always-encrypted-enclaves-enable-for-encrypted-columns.md)
- [Créer et utiliser des index sur des colonnes à l’aide d’Always Encrypted avec enclaves sécurisées](always-encrypted-enclaves-create-use-indexes.md)


