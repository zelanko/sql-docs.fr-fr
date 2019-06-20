---
title: Paramètres (Conversion) (MySQLToSQL) du projet | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 7ad5fe44-6445-4ba8-a457-5af792631f11
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 12e2e61c6b55bf3c549c08f2b090059d674ed83d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63162026"
---
# <a name="project-settings-conversion-mysqltosql"></a>Paramètres du projet (Conversion) (MySQLToSQL)
La page de Conversion de la **paramètres du projet** boîte de dialogue contient les paramètres qui personnalisent comment SSMA convertit la syntaxe de MySQL à la syntaxe SQL Server ou SQL Azure.  
  
Le volet de la Conversion est disponible dans le **paramètres du projet** et **par défaut des paramètres de projet** boîtes de dialogue.  
  
-   Utilisez le **par défaut des paramètres de projet** boîte de dialogue pour définir les options de configuration pour tous les projets. Pour accéder aux paramètres de conversion, sur le **outils** menu, sélectionnez **par défaut des paramètres de projet**, sélectionnez le type de projet de migration pour lequel les paramètres sont requis pour être affiché / a été remplacée par  **Version cible de migration** liste déroulante, cliquez sur **général** en bas du volet gauche, puis sélectionnez **Conversion**.  
  
-   Pour spécifier les paramètres pour le projet actuel, sur le **outils** menu, cliquez sur **paramètres du projet**, puis cliquez sur **général** en bas du volet gauche, puis cliquez sur **Conversion**.  
  
## <a name="options"></a>Options  
  
### <a name="collate-clause"></a>Collate, Clause  
  
|||  
|-|-|  
|**Terme**|**Définition**|  
|**Conversion de la clause COLLATE explicite**|Option de conversion de clause COLLATE explicite spécifie comment convertir des clauses COLLATE explicites dans le code de MySQL. Choix possibles : Ignorer et marquer avec un message d’avertissement / génèrent une erreur<br /><br />**Par défaut en Mode**:  Ignorer et d’interrogation avec un avertissement<br /><br />**Mode optimiste**:  Ignorer et d’interrogation avec un avertissement<br /><br />**Mode plein**:  Ignorer et d’interrogation avec un avertissement|  
  
### <a name="column-constraints"></a>Contraintes de colonne  
  
|||  
|-|-|  
|**Terme**|**Définition**|  
|**Générer de contrainte pour les colonnes de type de données d’ENUM**|Génère la contrainte pour les colonnes de type ENUM dans la table SQL Server ou SQL Azure, si elle n’est pas présent dans la table MySQL. Si Oui, toutes les colonnes convertis ENUM du type de données seront accompagnés de contrôle de la valeur de contrainte de validation.<br /><br />**Par défaut en Mode**:   Non<br /><br />**Mode optimiste**:  Non<br /><br />**Mode plein**:   Oui|  
|**Générer de contrainte pour les colonnes de type de données de jeu**|Génère la contrainte pour les colonnes de type de données défini dans la table SQL Server ou SQL Azure, si elle n’est pas présent dans la table MySQL. Si Oui, toutes les colonnes converties du type de données défini seront accompagnés de contrôle de la valeur de contrainte de validation.<br /><br />**Par défaut en Mode**:   Non<br /><br />**Mode optimiste**:  Non<br /><br />**Mode plein**:   Oui|  
|**Générer de contrainte pour les colonnes de colonnes de type de données numérique non signé**|Ajouter la vérification de valeur non négative aux colonnes de types de données numériques non signé.<br /><br />**Par défaut en Mode**:   Non<br /><br />**Mode optimiste**:  Non<br /><br />**Mode plein**:   Oui|  
|**Générer de contrainte pour les colonnes de type de données année**|Génère la contrainte pour les colonnes de type de données année dans la table SQL Server ou SQL Azure, si elle n’est pas présent dans la table MySQL. Si Oui, tous convertis en colonnes de données de l’année type sera associée avec contrôle de la valeur de contrainte de validation.<br /><br />**Par défaut en Mode**:   Non<br /><br />**Mode optimiste**:  Non<br /><br />**Mode plein**:   Oui|  
  
### <a name="data-types"></a>Types de données  
  
|||  
|-|-|  
|**Terme**|**Définition**|  
|**Conversion de types de données ENUM**|Spécifie comment le type de données MySQL ENUM doit être converti en tant que de convertir en NVARCHAR ou convertir en type numérique<br /><br />**Par défaut en Mode**:  Convertir en NVARCHAR<br /><br />**Mode optimiste**:  Convertir en NVARCHAR<br /><br />**Mode plein**:  Convertir en NVARCHAR|  
|**Conversion de type de jeu de données**|Spécifie comment MySQL définir le type de données doit être converti, convertir à NVARCHAR (L) / convertir BINARY(L)<br /><br />**Par défaut en Mode**: Convertir en NVARCHAR(L)<br /><br />**Mode optimiste**: Convertir en NVARCHAR(L)<br /><br />**Mode plein**: Convertir en NVARCHAR(L)|  
  
### <a name="generic"></a>Générique  
  
|||  
|-|-|  
|**Terme**|**Définition**|  
|**Colonnes sans valeur par défaut dans INSERT et remplacer**|Si Oui, toutes les instructions qui référencent des tables à l’aide de moteurs stockées autres que MyISAM et InnoDb doivent être marquées avec les messages d’avertissement conversion.<br /><br />**Par défaut en Mode**:  Ajouter à la liste des colonnes<br /><br />**Mode optimiste**:  Ajouter à la liste des colonnes<br /><br />**Mode plein**:   Ajouter à la liste des colonnes|  
|**Division par zéro génère de Conversion**|Spécifie s’il faut émuler MySQL sans comportement ERROR_FOR_DIVISION_BY_ZERO.<br /><br />**Par défaut en Mode**:   Error<br /><br />**Mode optimiste**:  Error<br /><br />**Mode plein**:   NULL|  
|**Opérateur IN**|Spécifie la manière de convertir l’opérateur IN de MySQL.<br /><br />**Par défaut en Mode**:   Toujours convertir en<br /><br />**Mode optimiste**:  Toujours convertir en<br /><br />**Mode plein**:   Développez si nécessaire|  
|**Conversion de MySQL (fonction)**|Spécifie comment convertir des fonctions standards de MySQL.<br /><br />**Par défaut en Mode**:   Optimistic<br /><br />**Mode optimiste**:  Optimistic<br /><br />**Mode plein**:   Précise|  
|**Non pris en charge de moteurs de stockage**|Si Oui, toutes les instructions qui référencent des tables à l’aide de moteurs stockées autres que MyISAM et InnoDb doivent être marquées avec les messages d’avertissement conversion.<br /><br />**Par défaut en Mode**:   Non<br /><br />**Mode optimiste**:  Non<br /><br />**Mode plein**:   Oui|  
|**Supprimer la génération de colonne auxiliaire ROWID**|Si Oui, interdit la création de la création de colonne auxiliaire ROWD sur les tables cibles. Peut affecter la migration de certaines structures.<br /><br />**Par défaut en Mode**:   Non<br /><br />**Mode optimiste**:  Non<br /><br />**Mode plein**:   Non|  
|**Conversion de l’instruction de troncation**|Spécifie comment convertir les instructions TRUNCATE.<br /><br />**Par défaut en Mode**:   TRUNCATE<br /><br />**Mode optimiste**:  TRUNCATE<br /><br />**Mode plein**:   TRUNCATE|  
  
### <a name="misc"></a>Divers  
  
|||  
|-|-|  
|**Terme**|**Définition**|  
|**Mappage de schéma par défaut**|Spécifie comment mapper des bases de données MySQL en schémas SQL Server.<br /><br />**Par défaut en Mode**:  Base de données à la base de données<br /><br />**Mode optimiste**:  Base de données à la base de données<br /><br />**Mode plein**:  Base de données à la base de données|  
  
### <a name="procedures-and-functions"></a>Procédures et fonctions  
  
|||  
|-|-|  
|**Terme**|**Définition**|  
|**Conversion de fonction par défaut**|Indique si les fonctions doivent être par défaut être converties pour les fonctions T-SQL ou à des procédures stockées.<br /><br />**Par défaut en Mode**:  Convertir (fonction)<br /><br />**Mode optimiste**:  Convertir (fonction)<br /><br />**Mode plein**:  Convertir (fonction)|  
|**Générer un SET XACT_ABORT sur**|Spécifie si SET XACT_ABORT ON doit être ajouté au début de la procédure converti ou du déclencheur.<br /><br />**Par défaut en Mode**:  Oui<br /><br />**Mode optimiste**:  Oui<br /><br />**Mode plein**:  Oui|  
|**Générer un SET NOCOUNT sur**|Spécifie si SET NOCOUNT ON doit être ajouté au début de la procédure converti ou du déclencheur.<br /><br />**Par défaut en Mode**:  Oui<br /><br />**Mode optimiste**:  Oui<br /><br />**Mode plein**:  Oui|  
  
### <a name="spatial-data-types"></a>Types de données spatiales  
  
|||  
|-|-|  
|**Terme**|**Définition**|  
|**Par défaut de la zone englobante {XMAX&#124;XMIN&#124;YMAX&#124;YMIN} pour les index spatiaux**|Définit la valeur par défaut pour {XMAX&#124;XMIN&#124;YMAX&#124;YMIN} le paramètre du cadre englobant utilisé dans les index spatiaux.<br /><br />**Mode par défaut**<br /><br />XMAX : 100<br /><br />XMIN : 0<br /><br />YMAX : 100<br /><br />YMIN : 0<br /><br />**Mode optimiste**<br /><br />XMAX : 100<br /><br />XMIN : 0<br /><br />YMAX :  100<br /><br />YMIN : 0<br /><br />**Mode complet**<br /><br />XMAX : 100<br /><br />XMIN : 0<br /><br />YMAX : 100<br /><br />YMIN : 0|  
|**Densité de grille par défaut pour les index spatiaux**|Définit la valeur par défaut pour LEVEL_1, LEVEL_2, LEVEL_3 et LEVEL_4 de densité de grille utilisée dans les index spatiaux.<br /><br />**Mode par défaut**<br /><br />LEVEL_1 : Par défaut<br /><br />LEVEL_2 : Par défaut<br /><br />LEVEL_3 : Par défaut<br /><br />LEVEL_4 : Par défaut<br /><br />**Mode optimiste**<br /><br />LEVEL_1 : Par défaut<br /><br />LEVEL_2 : Par défaut<br /><br />LEVEL_3 : Par défaut<br /><br />LEVEL_4 : Par défaut<br /><br />**Mode complet**<br /><br />LEVEL_1 : Par défaut<br /><br />LEVEL_2 : Par défaut<br /><br />LEVEL_3 : Par défaut<br /><br />LEVEL_4 : Par défaut|  
  
### <a name="transactions"></a>Transactions  
  
|||  
|-|-|  
|**Terme**|**Définition**|  
|**Tables non transactionnel**|Spécifie si toutes les références à la table qui ne prennent pas en charge les transactions doivent être marquées avec des messages d’avertissement conversion.<br /><br />**Par défaut en Mode**: Non<br /><br />**Mode optimiste**: Non<br /><br />**Mode plein**: Oui|  
|**Niveau d’isolation de transaction**|Spécifie le niveau d’isolation de transaction doit être utilisé pour les nouvelles transactions.<br /><br />**Par défaut en Mode**:   Par défaut<br /><br />**Mode optimiste**:  Par défaut<br /><br />**Mode plein**:   Lecture renouvelable|  
  
### <a name="value-control"></a>Contrôle de valeur  
  
|||  
|-|-|  
|**Terme**|**Définition**|  
|**Caractère à la conversion numérique**|Spécifie comment gérer les conversions implicites et explicites à partir du type de données caractères pour les types de données numériques.<br /><br />**Par défaut en Mode**:   Optimistic<br /><br />**Mode optimiste**:  Optimistic<br /><br />**Mode plein**:   Précise|  
|**Contrôler les valeurs numériques non SIGNÉS**|Contrôle affectant des valeurs aux paramètres et les variables numériques non SIGNÉS.<br /><br />**Par défaut en Mode**:   Non<br /><br />**Mode optimiste**:  Non<br /><br />**Mode plein**:   Oui|  
|**Soustraction de non signé de contrôle**|Modifier les valeurs négatives dans les colonnes de table de type de données non signé.<br /><br />**Par défaut en Mode**:   Convertir ' en tant que-est »<br /><br />**Mode optimiste**:  Convertir ' en tant que-est »<br /><br />**Mode plein**:   Marquer avec un avertissement|  
|**Conversion vers et depuis le type de données binaires**|Spécifie comment gérer les conversions implicites et explicites à partir du type de données binaires.<br /><br />**Par défaut en Mode**:   Optimistic<br /><br />**Mode optimiste**:  Optimistic<br /><br />**Mode plein**:   Précise|  
|**Type de conversion de données de Date/heure**|Spécifie comment gérer les conversions implicites et explicites en Date/heure de type de données.<br /><br />**Par défaut en Mode**:   Émuler le format de MySQL<br /><br />**Mode optimiste**:  Utiliser le format SQL Server<br /><br />**Mode plein**:   Émuler le format de MySQL|  
|**Littéraux numériques avec une précision supérieure à 38**|Spécifie comment convertir des littéraux numériques avec une précision supérieure à 38.<br /><br />**Par défaut en Mode**:   Arrondir si Possible<br /><br />**Mode optimiste**:  Arrondir si Possible<br /><br />**Mode plein**:   Arrondir si Possible|  
|**Date de zéro dans les colonnes NOT NULL**|Spécifie comment gérer l’affectation de colonnes NOT NULL de zéro-date, date de zéro ou de valeurs de date/heure non valide.<br /><br />**Par défaut en Mode**:   GETDATE()<br /><br />**Mode optimiste**:  GETDATE()<br /><br />**Mode plein**:   GETDATE()|  
  
## <a name="see-also"></a>Voir aussi  
[Référence de l’Interface utilisateur &#40;MySQLToSQL&#41;](../../ssma/mysql/user-interface-reference-mysqltosql.md)  
  
