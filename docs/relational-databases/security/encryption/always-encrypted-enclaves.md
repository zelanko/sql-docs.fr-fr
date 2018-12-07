---
title: Always Encrypted avec enclaves sécurisées (moteur de base de données) | Microsoft Docs
ms.custom: ''
ms.date: 09/24/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
author: jaszymas
ms.author: jaszymas
manager: craigg
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 9dfc5e2cf7bab164d650f2da1767b2a0e7c399aa
ms.sourcegitcommit: c7febcaff4a51a899bc775a86e764ac60aab22eb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2018
ms.locfileid: "52711180"
---
# <a name="always-encrypted-with-secure-enclaves"></a>Always Encrypted avec enclaves sécurisées
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]


Always Encrypted avec enclaves sécurisées fournit des fonctionnalités supplémentaires à la fonction [Always Encrypted](always-encrypted-database-engine.md).

Introduit dans SQL Server 2016, Always Encrypted protège la confidentialité des données sensibles contre les programmes malveillants et les utilisateurs *non autorisés* à privilèges élevés de SQL Server. Les utilisateurs non autorisés à privilèges élevés sont les administrateurs de bases de données (DBA), les administrateurs d’ordinateurs, les administrateurs de cloud ou toute autre personne qui a un accès légitime aux instances de serveur, au matériel, etc., mais ne devant pas avoir accès à tout ou partie des données réelles. 

Jusqu’à présent, Always Encrypted protégeait les données en les chiffrant côté client et en n’autorisant jamais les données ou les clés de chiffrement correspondantes à s’afficher en texte clair dans le moteur SQL Server. Par conséquent, la fonctionnalité sur des colonnes chiffrées à l’intérieur de la base de données était extrêmement limitée. Les seules opérations que SQL Server pouvait effectuer sur des données chiffrées étaient les comparaisons d’égalité (et les comparaisons d’égalité n’étaient disponibles qu’avec le chiffrement déterministe). Toutes les autres opérations, notamment les opérations de chiffrement (chiffrement des données initiales ou rotation de clé) ou les calculs riches (par exemple, les critères spéciaux), n’étaient pas prises en charge à l’intérieur de la base de données. Les utilisateurs devaient déplacer les données en dehors de la base de données pour effectuer ces opérations côté client.

Always Encrypted *avec enclaves sécurisées* résout ces limitations en autorisant les calculs sur les données de texte en clair à l’intérieur d’une enclave sécurisée côté serveur. Une enclave sécurisée est une région de mémoire protégée dans le processus SQL Server qui agit comme un environnement d’exécution approuvé pour le traitement des données sensibles dans le moteur SQL Server. Une enclave sécurisée apparaît sous la forme d’une boîte noire pour le reste de SQL Server et des autres processus sur l’ordinateur d’hébergement. Il n’existe aucun moyen d’afficher les données ou le code à l’intérieur de l’enclave depuis l’extérieur, même avec un débogueur.  


Always Encrypted utilise des enclaves sécurisées, comme illustré dans le diagramme suivant :

![flux de données](./media/always-encrypted-enclaves/ae-data-flow.png)



Lors de l’analyse de la requête d’une application, le moteur SQL Server détermine si la requête contient des opérations sur les données chiffrées qui nécessitent l’utilisation de l’enclave sécurisée. Pour les requêtes où l’enclave sécurisée doit être accessible :

- Le pilote client envoie les clés de chiffrement de colonne requises pour les opérations à l’enclave sécurisée (via un canal sécurisé). 
- Ensuite, le pilote client soumet la requête pour exécution, ainsi que les paramètres de la requête chiffrée.

Pendant le traitement de la requête, les données ou les clés de chiffrement de colonne ne sont pas exposées en texte clair dans le moteur SQL Server en dehors de l’enclave sécurisée. Le moteur SQL Server délègue les opérations de chiffrement et les calculs sur les colonnes chiffrées à l’enclave sécurisée. Si nécessaire, l’enclave sécurisée déchiffre les paramètres de la requête et/ou les données stockées dans les colonnes chiffrées et effectue les opérations demandées.

## <a name="why-use-always-encrypted-with-secure-enclaves"></a>Pourquoi utiliser Always Encrypted avec enclaves sécurisées ?

Avec les enclaves sécurisées, Always Encrypted protège la confidentialité des données sensibles, tout en offrant les avantages suivants :

- **Chiffrement sur place** : les opérations de chiffrement des données sensibles (par exemple, le chiffrement des données initiales ou la permutation d’une clé de chiffrement de colonne) sont effectuées à l’intérieur de l’enclave sécurisée et ne nécessitent pas le déplacement des données en dehors de la base de données. Vous pouvez émettre le chiffrement sur place à l’aide de l’instruction Transact-SQL ALTER TABLE, et vous n’avez pas besoin d’utiliser des outils, comme l’Assistant Always Encrypted dans SSMS ou la cmdlet PowerShell Set-SqlColumnEncryption.

- **Calculs riches (préversion)**  : les opérations sur des colonnes chiffrées, notamment les critères spéciaux (prédicat LIKE) et les comparaisons de plages, sont prises en charge à l’intérieur de l’enclave sécurisée, ce qui rend Always Encrypted accessible à une large gamme d’applications et de scénarios qui requièrent que ces calculs s’effectuent dans le système de base de données.

> [!IMPORTANT]
> Dans [!INCLUDE[sql-server-2019](../../../includes/sssqlv15-md.md)], les calculs riches sont en attente de plusieurs optimisations des performances, incluent des fonctionnalités limitées (aucune indexation, etc.) et sont actuellement désactivés par défaut. Pour activer les calculs riches, consultez [Activer les calculs riches](configure-always-encrypted-enclaves.md#configure-a-secure-enclave).

Dans [!INCLUDE[sql-server-2019](../../../includes/sssqlv15-md.md)], Always Encrypted avec enclaves sécurisées utilise des enclaves mémoire sécurisées de [sécurité basée sur la virtualisation (VBS)](https://cloudblogs.microsoft.com/microsoftsecure/2018/06/05/virtualization-based-security-vbs-memory-enclaves-data-protection-through-isolation/), également appelées mode sécurisé virtuel ou enclaves VSM, dans Windows.

## <a name="secure-enclave-attestation"></a>Attestation d’enclave sécurisée

L’enclave sécurisée à l’intérieur du moteur SQL Server peut accéder aux données sensibles stockées dans les colonnes de base de données chiffrées et les clés de chiffrement de colonne correspondantes en texte en clair. Avant de soumettre une requête qui implique des calculs d’enclave à SQL Server, le pilote client à l’intérieur de l’application doit vérifier que l’enclave sécurisée est une enclave authentique basée sur une technologie donnée (par exemple, VBS) et que le code s’exécutant à l’intérieur de l’enclave a été signé pour s’exécuter à l’intérieur de l’enclave. 

Le processus de vérification de l’enclave est appelé **attestation d’enclave**, et il implique généralement qu’un pilote client dans l’application (et parfois également SQL Server) contacte un service d’attestation externe. Les détails du processus d’attestation dépendent de la technologie de l’enclave et du service d’attestation.

Le processus d’attestation pris en charge par SQL Server pour les enclaves sécurisées VBS dans [!INCLUDE[sql-server-2019](../../../includes/sssqlv15-md.md)] est l’attestation de runtime Windows Defender System Guard, qui utilise le service HGS (Host Guardian Service) comme service d’attestation. Vous devez configurer SGH dans votre environnement et inscrire l’ordinateur qui héberge votre instance SQL Server dans SGH. Vous devez également configurer vos outils ou applications client (par exemple, SQL Server Management Studio) avec une attestation SGH.

## <a name="secure-enclave-providers"></a>Fournisseurs d’enclave sécurisée

Pour utiliser Always Encrypted avec enclaves sécurisées, une application doit utiliser un pilote client qui prend en charge la fonctionnalité. Dans [!INCLUDE[sql-server-2019](../../../includes/sssqlv15-md.md)], vos applications doivent utiliser .NET Framework 4.7.2 et le fournisseur de données .NET Framework pour SQL Server. En outre, les applications .NET doivent être configurées avec un **fournisseur d’enclave sécurisée** spécifique au type de l’enclave (par exemple, VBS) et au service d’attestation (par exemple, SGH), que vous utilisez. Les fournisseurs d’enclave pris en charge sont expédiés séparément dans un package NuGet, que vous devez intégrer à votre application. Un fournisseur d’enclave implémente la logique côté client pour le protocole d’attestation et pour établir un canal sécurisé avec une enclave sécurisée d’un type donné.

## <a name="enclave-enabled-keys"></a>Clés prenant en charge l’enclave

Always Encrypted avec enclaves sécurisées introduit le concept des clés prenant en charge l’enclave :

- **Clé principale de colonne prenant en charge l’enclave** : clé principale de colonne qui possède la propriété ENCLAVE_COMPUTATIONS spécifiée dans l’objet de métadonnées de la clé principale de colonne à l’intérieur de la base de données. L’objet de métadonnées de la clé principale de colonne doit également contenir une signature valide des propriétés des métadonnées.
- **Clé de chiffrement de colonne prenant en charge l’enclave** : clé de chiffrement de colonne qui est chiffrée avec une clé principale de colonne prenant en charge l’enclave.

Lorsque le moteur SQL Server détermine les opérations, spécifiées dans une requête, qui doivent être effectuées à l’intérieur de l’enclave sécurisée, le moteur SQL Server demande que le pilote client partage les clés de chiffrement de colonne qui sont nécessaires pour les calculs avec l’enclave sécurisée. Le pilote client partage les clés de chiffrement de colonne uniquement si les clés prennent en charge l’enclave (c’est-à-dire qu’elles sont chiffrées avec des clés principales de colonne prenant en charge l’enclave) et qu’elles sont correctement signées. Sinon, la requête échoue.

## <a name="enclave-enabled-columns"></a>Colonnes prenant en charge l’enclave

Une colonne prenant en charge l’enclave est une colonne de base de données qui est chiffrée avec une clé de chiffrement de colonne prenant en charge l’enclave. La fonctionnalité disponible pour une colonne prenant en charge l’enclave varie selon le type de chiffrement que la colonne utilise.

- **Chiffrement déterministe** : les colonnes prenant en charge l’enclave utilisant le chiffrement déterministe prennent en charge le chiffrement sur place, mais aucune autre opération à l’intérieur de l’enclave sécurisée. La comparaison d’égalité est prise en charge, mais est effectuée en dehors de l’enclave, en comparant le texte chiffré (en dehors de l’enclave).  
- **Chiffrement aléatoire** : les colonnes prenant en charge l’enclave utilisant le chiffrement aléatoire prennent en charge le chiffrement sur place, ainsi que les calculs riches à l’intérieur de l’enclave sécurisée. Les calculs riches pris en charge sont les critères spéciaux et les [opérateurs de comparaison](https://docs.microsoft.com/sql/t-sql/language-elements/comparison-operators-transact-sql), notamment la comparaison d’égalité.

Pour plus d’informations sur les types de chiffrement, consultez [Chiffrement Always Encrypted](always-encrypted-cryptography.md).

Le tableau suivant récapitule les fonctionnalités disponibles pour les colonnes chiffrées, selon que les colonnes utilisent des clés de chiffrement de colonne prenant en charge l’enclave et un type de chiffrement.

| **Opération**| **La colonne ne prend PAS en charge l’enclave** |**La colonne ne prend PAS en charge l’enclave**| **La colonne prend en charge l’enclave**  |**La colonne prend en charge l’enclave** |
|:---|:---|:---|:---|:---|
| | **Chiffrement aléatoire**  | **Chiffrement déterministe**     | **Chiffrement aléatoire**      | **Chiffrement déterministe**     |
| **Chiffrement sur place** | Non pris en charge  | Non pris en charge   | Pris en charge         | Pris en charge    |
| **Comparaison d’égalité**   | Non pris en charge | Pris en charge en dehors de l’enclave | Pris en charge (à l’intérieur de l’enclave) | Pris en charge en dehors de l’enclave |
| **Opérateurs de comparaison au-delà de l’égalité** | Non pris en charge  | Non pris en charge   | Pris en charge      | Non pris en charge     |
| **LIKE**    | Non pris en charge      | Non pris en charge    | Pris en charge     | Non pris en charge    |

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

## <a name="known-limitations"></a>Limitations connues

Limitations générales : 

- Toutes les limitations répertoriées pour la version actuelle d’Always Encrypted sous [Informations sur les fonctionnalités](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine#feature-details) s’appliquent également à Always Encrypted avec enclaves sécurisées (pour les colonnes chiffrées avec des clés prenant en charge l’enclave), sauf les restrictions qui sont supprimées avec l’ajout de la prise en charge du chiffrement sur place et des calculs riches.

- La comparaison d’égalité reste le seul opérateur Transact-SQL pris en charge avec le chiffrement déterministe et les comparaisons d’égalité sont effectuées en comparant les valeurs de texte chiffré en dehors de l’enclave, peu importe si la clé de chiffrement de colonne prend en charge l’enclave ou pas. La seule nouvelle fonctionnalité qui est déverrouillée avec les clés de chiffrement de colonne prenant en charge l’enclave pour le chiffrement déterministe, sont les opérations de chiffrement sur place. Si vous avez une colonne qui est chiffrée à l’aide du chiffrement déterministe (et une clé ne prenant pas en charge l’enclave), pour permettre des calculs riches (critères spéciaux, opérations de comparaison), vous devez chiffrer à nouveau la colonne à l’aide du chiffrement aléatoire.

- La restriction existante sur l’utilisation de classements s’applique aux colonnes chiffrées avec des clés de chiffrement de colonne prenant en charge l’enclave : les colonnes de chaîne de caractères (char, nchar, varchar, nvarchar) chiffrées à l’aide du chiffrement déterministe doivent utiliser des classements avec un ordre de tri binaire 2 (classements BIN2). Les colonnes de chaîne de caractères utilisant des classements non-BIN2 peuvent être chiffrées à l’aide du chiffrement aléatoire. Cependant, la seule nouvelle fonctionnalité activée pour ces colonnes (si elles sont chiffrées avec des clés de chiffrement de colonne prenant en charge l’enclave) est le chiffrement sur place. **Pour prendre en charge les calculs riches (critères spéciaux, opérations de comparaison), une colonne doit utiliser un classement BIN2** (et la colonne doit être chiffrée à l’aide du chiffrement aléatoire et d’une clé de chiffrement de colonne prenant en charge l’enclave).

- L’utilisation de clés prenant en charge l’enclave pour les colonnes dans des tables en mémoire n’est pas prise en charge.

- Les opérations de chiffrement sur place ne peuvent pas être combinées avec d’autres modifications des métadonnées de la colonne, à l’exception des modifications de classement et la possibilité de valeur null. Par exemple, vous ne pouvez pas chiffrer, chiffrer à nouveau ou déchiffrer une colonne ET modifier un type de données de la colonne dans une instruction Transact-SQL ALTER TABLE ou ALTER COLUMN unique. Vous devez utiliser deux instructions distinctes.

Les limitations suivantes s’appliquent à la préversion actuelle, mais il est prévu de les résoudre :

- Les colonnes prenant en charge l’enclave utilisant le chiffrement aléatoire ne peuvent pas être indexées, ce qui signifie que les opérations de comparaison ou les opérations LIKE nécessitent des analyses de la table.

- Le seul pilote client prenant en charge Always Encrypted avec enclaves sécurisées est le fournisseur de données .NET Framework pour SQL Server (ADO.NET) dans .NET Framework 4.7.2. Il n’y a pas de prise en charge pour ODBC/JDBC.

- Les seuls magasins de clés pris en charge pour le stockage des clés principales de colonne prenant en charge l’enclave sont le Magasin de certificats Windows et Azure Key Vault.

- Actuellement, la prise en charge des outils pour Always Encrypted avec enclaves sécurisées est incomplète. Pour déclencher une opération de chiffrement sur place via une instruction Transact-SQL ALTER TABLE, vous devez émettre l’instruction à l’aide d’une fenêtre de requête dans SSMS, ou vous pouvez écrire votre propre programme qui émet l’instruction. La cmdlet Set-SqlColumnEncryption dans le module PowerShell SqlServer et l’Assistant Always Encrypted dans SQL Server Management Studio ne prennent pas encore en charge le chiffrement sur place. Actuellement, ces deux outils déplacement les données en dehors de la base de données pour les opérations de chiffrement, même si les clés de chiffrement de colonne utilisées pour les opérations prennent en charge l’enclave. 

## <a name="known-issues"></a>Problèmes connus

- Les calculs riches sur les colonnes de chaîne non UNICODE (char, varchar) requièrent qu'un classement BIN2 soit défini au niveau de la base de données. Consultez les Considérations spéciales pour les colonnes de chaîne non UNICODE dans [Gérer les classements](configure-always-encrypted-enclaves.md#manage-collations).

## <a name="next-steps"></a>Next Steps

- Configurer votre environnement de test et tester la fonctionnalité Always Encrypted avec enclaves sécurisées dans SSMS. Consultez [Tutoriel : Bien démarrer avec Always Encrypted avec enclaves sécurisées en utilisant SSMS](../tutorial-getting-started-with-always-encrypted-enclaves.md).