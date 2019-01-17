---
title: Masquage statique des données | Microsoft Docs
ms.date: 11/05/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: a62f4ff9-2953-42ca-b7d8-1f8f527c4d66
author: egranet
ms.author: aliceku
manager: ajayj
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: cec6c79fadb5ef2a63145fff3efe0df3c8cd0f9d
ms.sourcegitcommit: 467b2c708651a3a2be2c45e36d0006a5bbe87b79
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53980455"
---
# <a name="static-data-masking"></a>Masquage statique des données
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Le masquage statique des données est un composant de [SQL Server Management Studio](../../ssms/sql-server-management-studio-ssms.md)18.0 Preview 5 et versions ultérieures. La dernière préversion de SQL Server Management Studio peut être téléchargée [ici](../../ssms/download-sql-server-management-studio-ssms.md). 

![Masquage statique des données](../../relational-databases/security/media/sql-static-data-masking/static_data_masking_intro_image.PNG)


## <a name="what-is-static-data-masking"></a>Qu’est-ce que le masquage statique des données ? 
Le masquage statique des données est une fonctionnalité de SQL Server Management Studio qui permet aux utilisateurs de créer une copie masquée d’une base de données. Cette fonctionnalité a été développée pour les organisations qui doivent partager des données, dont des données sensibles, entre des équipes ou avec d’autres organisations. 

En remplaçant les données sensibles (données avant masquage) par de nouvelles données (données après masquage), le masquage statique des données contribue au traitement des scénarios suivants : 
- Développement et test 
- Analytique et rapports d’entreprise 
- Dépannage 
- Partage de la base de données avec un consultant, une équipe de recherche ou un tiers 

L’exemple ci-dessous illustre le fonctionnement du masquage statique des données. Avant le masquage, la colonne contient des numéros de sécurité sociale. Après le masquage, les cinq premiers chiffres de chaque numéro de sécurité sociale ont été remplacés par des chiffres générés de façon aléatoire.

| Numéro de sécurité sociale aux États-Unis (avant masquage)   | Numéro de sécurité sociale aux États-Unis (après masquage)  |
| ------------- | ------------- |
| 140-38-9110 | 302-92-9110 |
| 463-34-5535 | 189-70-5535 |
| 116-30-8733 | 201-01-8733 |
| 209-36-1971 | 683-10-1971 |
| 372-38-6948 | 372-38-6948 |
| 267-64-2334 | 100-03-2334 |
| 523-93-4176 | 582-20-4176 |
| 573-91-5137 | 730-20-5137 |
| 612-72-1026 | 369-40-1026 |

Les utilisateurs du masquage statique des données peuvent choisir parmi plusieurs fonctions de masquage. En fonction de la fonction de masquage, les données avant masquage et après masquage peuvent présenter un lien fort ou aucun lien du tout. Une fonction de masquage qui effectue un réarrangement fournit des données après masquage fortement liées aux données avant masquage. 

| Numéro de sécurité sociale aux États-Unis (avant masquage) | Numéro de sécurité sociale aux États-Unis (après masquage) |
| ------------- | ------------- |
| 140-38-9110 | 612-72-1026 |  
| 463-34-5535 | 372-38-6948 | 
| 116-30-8733 | 523-93-4176 |
| 209-36-1971 | 209-36-1971 | 
| 372-38-6948 | 140-38-9110 |
| 267-64-2334 | 463-34-5535 | 
| 523-93-4176 | 573-91-5137 | 
| 573-91-5137 | 267-64-2334 | 
| 612-72-1026 | 116-30-8733 |

Une fonction de masquage qui effectue un remplacement avec une valeur NULL fournit des données après masquage non liées aux données avant masquage. 
 
| Numéro de sécurité sociale aux États-Unis (avant masquage) | Numéro de sécurité sociale aux États-Unis (après masquage) |
| ------------- | ------------- |
| 140-38-9110 | NULL |  
| 463-34-5535 | NULL | 
| 116-30-8733 | NULL |
| 209-36-1971 | NULL | 
| 372-38-6948 | NULL |
| 267-64-2334 | NULL | 
| 523-93-4176 | NULL | 
| 573-91-5137 | NULL | 
| 612-72-1026 | NULL |

## <a name="how-does-static-data-masking-work"></a>Fonctionnement du masquage statique des données
Le masquage statique des données intervient au niveau des colonnes. Les utilisateurs sélectionnent les colonnes qu’ils souhaitent masquer et, pour chaque colonne sélectionnée, la fonction de masquage qu’ils souhaitent appliquer. Plusieurs fonctions de masquage sont proposées. Elles sont décrites en détail dans la section [Fonctions de masquage](#masking-functions). 

Le masquage statique des données crée ensuite une copie de la base de données. Pour Azure SQL Database, la copie s’effectue via la [fonction copy](https://azure.microsoft.com/blog/static-data-masking-preview/). Pour SQL Server, elle s’effectue via une opération de sauvegarde suivie d’une opération de restauration. À partir de là, pour chaque colonne, le masquage statique des données commence à remplacer les données avant masquage par des données après masquage en fonction de la fonction de masquage sélectionnée. 

Le remplacement s’effectue au niveau du stockage. Par conséquent, il n’est pas possible de récupérer les données avant masquage à partir de la copie masquée de la base de données une fois le masquage statique des données effectué.

## <a name="how-to-guide"></a>Guide pratique

Voici un guide pas à pas pour l’exécution du masquage statique des données. 
 
1. Lancez SQL Server Management Studio. Connectez-vous à votre base de données. Dans le volet **Explorateur d’objets** sur le côté gauche, développez le dossier Bases de données. Cliquez avec le bouton droit sur la base de données que vous souhaitez masquer. Cliquez avec le bouton gauche sur **Tâches**. Cliquez avec le bouton gauche sur **Masquer la base de données... (préversion)**.
 
 ![Menu Tâches](../../relational-databases/security/media/sql-static-data-masking/task_data_masking.PNG)
 
2. La fenêtre de configuration du masquage apparaît. Elle affiche toutes les tables de la base de données. Ces tables sont présentées par schéma, puis triées par ordre alphabétique au sein d’un schéma. 
 
 ![Interface utilisateur](../../relational-databases/security/media/sql-static-data-masking/ui_dropdown.PNG)
 
3. Cliquez sur l’icône de liste déroulante à côté du nom de la table pour obtenir la liste de toutes les colonnes dans la table. Pour chaque colonne de la table, le type de données de la colonne est spécifié ainsi que si la colonne est Nullable. Une colonne Nullable est une colonne qui peut recevoir la valeur NULL en tant qu’entrée. 
 
 ![Liste déroulante de table](../../relational-databases/security/media/sql-static-data-masking/ui_dropdown_column.png)
 
4. Sélectionnez toutes les colonnes que vous souhaitez masquer et la fonction de masquage que vous souhaitez appliquer. Les types de masquage disponibles sont **Réarrangement**, **Réarrangement de groupe**, **Valeur unique**, **NULL**, **Chaîne composée**. 
 
 ![Liste déroulante des fonctions de masquage](../../relational-databases/security/media/sql-static-data-masking/masking_functions.PNG)
 
 REMARQUE : La plupart de ces fonctions de masquage ont des paramètres de configuration supplémentaires. Pour le masquage par réarrangement, la fonctionnalité Masquage statique des données fournit un paramètre par défaut. Pour le masquage par réarrangement de groupe, à valeur unique ou à chaîne composée, l’utilisateur doit fournir des paramètres de configuration. Pour modifier ou spécifier un paramètre de configuration, cliquez sur l’option **Configurer...** et attribuez une (autre) valeur au paramètre dans la boîte de dialogue qui s’affiche. Une description détaillée de chaque fonction de masquage est fournie dans [Fonctions de masquage](#masking-functions).
 
 ![Bouton de configuration des fonctions de masquage](../../relational-databases/security/media/sql-static-data-masking/masking_functions_configure.png)
 
 Les choix de configuration du masquage sont validés à la volée quant aux erreurs et avertissements de configuration et liés au schéma.  Tout ce qui est détecté s’affiche sur la gauche en tant qu’icône sur laquelle vous pouvez pointer la souris pour obtenir des détails supplémentaires. 
 
 Dans l’exemple ci-dessous, l’utilisateur a sélectionné le masquage NULL pour une colonne qui n’autorise pas les valeurs NULL (contrainte NOT NULL).
 
 ![Erreur du mécanisme de validation](../../relational-databases/security/media/sql-static-data-masking/validation_mechanism_error_message.PNG)
 
 Dans l’exemple ci-dessous, l’utilisateur a sélectionné le masquage par réarrangement de groupe pour une seule colonne. Comme le réarrangement de groupe requiert un minimum de deux colonnes, un avertissement est émis. 
 
 ![Avertissement du mécanisme de validation](../../relational-databases/security/media/sql-static-data-masking/validation_warning.PNG)
 
5. L’entière configuration de masquage peut être enregistrée dans un fichier XML pour une utilisation ultérieure.  La configuration des fonctions de masquage est identique pour les bases de données SQL Azure et les bases de données locales, mais il existe de légères différences quant à l’enregistrement d’autres propriétés (par exemple, le chemin d’accès du fichier de sauvegarde). Pour enregistrer la configuration, cliquez sur **Enregistrer la configuration**, fournissez un nom de fichier et cliquez sur Enregistrer.  Les utilisateurs peuvent charger ultérieurement un fichier de configuration existant à l’aide de **Charger la configuration**. Nous recommandons d’utiliser des fichiers de configuration pour les tables avec un grand nombre de colonnes. 
 
 ![Fichier de configuration](../../relational-databases/security/media/sql-static-data-masking/load_save_config.PNG)
 
6. Le masquage statique des données crée un dossier dans le dossier **Documents** de l’utilisateur, nommé Masquage statique des données et y place les fichiers journaux. Les fichiers journaux peuvent être utiles à des fins de débogage. Le nom du fichier journal est indiqué au bas de la fenêtre de configuration. 
  
 
7. (SQL Server uniquement) Si vous utilisez le masquage statique des données sur une base de données locale, cette fonctionnalité effectue une opération de sauvegarde/restauration. Dans **Étape 2 : Emplacement du fichier .BAK dupliqué**, indiquez l’emplacement sur le serveur où le fichier de sauvegarde sera stocké. 

## <a name="masking-functions"></a>Fonctions de masquage

### <a name="null-masking"></a>Masquage NULL

Le masquage NULL remplace toutes les valeurs dans la colonne par la valeur NULL. Si la colonne n’autorise pas les valeurs NULL, l’outil de masquage statique des données retourne une erreur. 

### <a name="single-value-masking"></a>Masquage à valeur unique

Le masquage à valeur unique remplace toutes les valeurs dans la colonne par une valeur fixe unique, spécifiée par l’utilisateur. Le format de l’entrée doit être convertible vers le type quelconque de la colonne sélectionnée. Pour spécifier la valeur, cliquez sur **Configurer...**, fournissez une valeur, puis cliquez sur **OK**. 

![Paramètre de masquage à valeur unique](../../relational-databases/security/media/sql-static-data-masking/single_value_parameter.PNG)


### <a name="shuffle-masking"></a>Masquage par réarrangement

Toutes les valeurs de la colonne sont réarrangées dans de nouvelles lignes. Aucune nouvelle donnée n’est générée. Le masquage par réarrangement fournit l’option de conserver les entrées de valeur NULL dans la colonne. Pour ce faire, cliquez sur **Configurer...** et cochez la case Conserver les positions NULL.

![Paramètre de masquage par réarrangement](../../relational-databases/security/media/sql-static-data-masking/shuffle_parameter.PNG)

Voici un exemple de masquage par réarrangement où les valeurs NULL ne conservent pas leur place, puis où elles conservent leur place.


| Numéro de sécurité sociale aux États-Unis (avant masquage) | Numéro de sécurité sociale aux États-Unis (après masquage avec réarrangement des entrées NULL) | Numéro de sécurité sociale aux États-Unis (après masquage avec non-réarrangement des entrées NULL) |
| ------------- | ------------- | ------------- |
| 116-30-8733 | 612-72-1026 | 463-34-5535 |
| 140-38-9110 | NULL | 573-91-5137  |
| 209-36-1971 | 523-93-4176 | 140-38-9110 |
| NULL | 209-36-1971 | NULL |
| 463-34-5535 | 140-38-9110 | 116-30-8733  |
| 523-93-4176 | 463-34-5535 | 612-72-1026  |
| NULL | 573-91-5137 | NULL |
| 573-91-5137 | NULL | 523-93-4176 |
| 612-72-1026  | 116-30-8733  | 209-36-1971 |  

### <a name="group-shuffle-masking"></a>Masquage par réarrangement de groupe
Le réarrangement de groupe lie plusieurs colonnes dans un groupe de lecture aléatoire. Les colonnes d’un groupe de réarrangement sont réarrangées ensemble. L’utilisateur doit spécifier le nom du groupe de réarrangement en utilisant l’option **Configurer...**

![Paramètre de masquage par réarrangement de groupe](../../relational-databases/security/media/sql-static-data-masking/group_shuffle_parameter.PNG)

Les réarrangements de groupe se produisent au sein d’une même table. Si le même nom de groupe de réarrangement est utilisé dans plusieurs tables, les deux réarrangements de groupe sont des actions indépendantes. Le nom du groupe doit être le même pour chaque colonne à inclure dans le groupe. Cette valeur respecte la casse. Plusieurs groupes de réarrangement (avec des noms différents) peuvent se produire dans la même table. 

### <a name="string-composite-masking"></a>Masquage à chaîne composée

Le masquage à chaîne composée génère des chaînes aléatoires selon un modèle. Il est conçu pour des chaînes qui doivent suivre un modèle prédéfini pour constituer une entrée valide. Par exemple, les numéros de sécurité sociale aux États-Unis ont le format 123-45-6789. La syntaxe pour le masquage à chaîne composée est spécifiée dans la boîte de dialogue dans laquelle l’utilisateur doit entrer le modèle.

![Paramètre de masquage à chaîne composée](../../relational-databases/security/media/sql-static-data-masking/string_composite.PNG)

Le masquage à chaîne composée fournit trois exemples de modèles qu’il est possible de tester en cliquant dessus. Si vous cliquez sur Numéro de téléphone, le champ de modèle est rempli automatiquement avec la formule requise pour générer des numéros de téléphone aléatoires aux États-Unis.

![Exemple de paramètre de masquage à chaîne composée](../../relational-databases/security/media/sql-static-data-masking/string_composite_phone_example.PNG)

Le masquage à chaîne composée a également un mode avancé qui permet de remplacer les sous-sections des données existantes par des chaînes générées selon un modèle. La partie remplacée de la chaîne est déterminée par le groupe de capture dans une expression régulière. Par exemple, la partie d’un e-mail liée au nom d’utilisateur peut être remplacée tout en conservant le domaine, ou le numéro de téléphone peut être remplacé en conservant l’indicatif régional. Plus d’informations sur les expressions régulières sont disponibles [ici](https://docs.microsoft.com/dotnet/standard/base-types/regular-expression-language-quick-reference).

![Exemple de paramètre de masquage avancé à chaîne composée](../../relational-databases/security/media/sql-static-data-masking/string_composite_advanced.PNG)

Le masquage à chaîne composée et son mode avancé peuvent uniquement servir pour des colonnes avec les [types de données](../../t-sql/data-types/data-types-transact-sql.md) char, varchar, text, nchar, nvarchar, ntext.

## <a name="limitations"></a>Limitations 

Le masquage statique des données présente les limitations suivantes :

- Le masquage statique des données ne prend pas en charge les bases de données dotées de [tables temporelles](../../relational-databases/tables/temporal-tables.md).

- Le masquage statique des données ne masque pas les tables [à mémoire optimisée](../../relational-databases/in-memory-oltp/introduction-to-memory-optimized-tables.md).

- Le masquage statique des données ne masque pas les [colonnes calculées](../../relational-databases/tables/specify-computed-columns-in-a-table.md) ni les colonnes d’[identité](../../t-sql/statements/create-table-transact-sql-identity-property.md).

- Le masquage statique des données ne prend pas en charge les bases de données Hyperscale SQL Azure.

- Le masquage statique des données ne prend pas en charge les types de données de géométrie ni de géographie. 

En outre, le masquage statique des données présente trois limitations de ses capacités de masquage :

- Le masquage statique des données ne met pas à jour les [statistiques d’histogramme](../../relational-databases/statistics/statistics.md). Par conséquent, la copie masquée de la base de données peut encore contenir des données sensibles dans les statistiques de l’histogramme une fois le masquage statique des données effectué. Envisagez d’exécuter [UPDATE STATISTICS](../../t-sql/statements/update-statistics-transact-sql.md) pour remédier à ce problème. 

- Si le masquage statique des données renvoie une erreur, toutes les opérations de masquage sont suspendues. La copie de la base de données n’est pas supprimée et peut contenir des informations sensibles. L’utilisateur est responsable de la suppression de la copie de la base de données si le masquage statique des données renvoie une erreur. 

- (SQL Server uniquement) Le ou les [fichiers de données](../../relational-databases/databases/database-files-and-filegroups.md) et le [fichier journal](../../relational-databases/logs/the-transaction-log-sql-server.md) peuvent encore contenir des données sensibles dans la mémoire non allouée une fois le masquage statique des données effectué. Ces données sensibles peuvent être récupérées avec un éditeur hexadécimal si l’accès aux fichiers de données et au fichier journal lui est accordé.

## <a name="see-also"></a> Voir aussi  
 [Dynamic Data Masking](../../relational-databases/security/dynamic-data-masking.md)   
 [Prise en main du masquage statique des données des bases de données SQL](https://azure.microsoft.com/documentation/articles/sql-database-static-data-masking-get-started/)  
