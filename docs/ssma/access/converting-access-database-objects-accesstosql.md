---
title: Convertir des objets de base de données Access (AccessToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Access databases
- Access databases, converting schemas
- conversion
- conversion, converting schemas
- indexes, altering
- metadata
- metadata, altering
- metadata, converting
- migrating databases, one-click
- one-click migration
- schemas
- schemas, converting
- SQL
- SQL, converting
- syntax
- syntax, converting
- tables, altering
- translating Access to SQL Azure
- translating Access to SQL Server
ms.assetid: e0ef67bf-80a6-4e6c-a82d-5d46e0623c6c
caps.latest.revision: 22
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 9519ef6b157b1f1d951b93c791f856d6066e7b19
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2018
ms.locfileid: "38981931"
---
# <a name="converting-access-database-objects-accesstosql"></a>Convertir des objets de base de données Access (AccessToSQL)
Une fois que vous avez ajouté des bases de données Access et connecté à [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou SQL Azure, SSMA affiche les métadonnées pour l’accès et [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou objets de base de données SQL Azure. Vous pouvez maintenant sélectionner les objets de base de données Access et puis de convertir les schémas dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou les schémas de SQL Azure.  
  
## <a name="the-conversion-process"></a>Le processus de Conversion  
Convertir des objets de base de données accepte les définitions d’objets à partir de l’accès aux métadonnées, les convertit en équivalent [!INCLUDE[tsql](../../includes/tsql_md.md)] syntaxe et charge ensuite ces informations dans le projet. Vous pouvez ensuite afficher le [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou objets de SQL Azure et leurs propriétés à l’aide de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou de l’Explorateur de métadonnées SQL Azure.  
  
> [!IMPORTANT]  
> Conversion d’objets ne crée pas les objets dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou SQL Azure. Uniquement, il convertit les définitions d’objet et stocke les informations dans le projet SSMA.  
  
Lors de la conversion, SSMA imprime l’état sur le volet de sortie et messages d’erreur, avertissement et d’information vers le volet Liste d’erreurs. Ces informations permettent de déterminer si vous devez modifier vos bases de données Access ou de votre processus de conversion pour obtenir les résultats de la conversion souhaitée. Vous pouvez également utiliser les informations contenues dans le [préparation de bases de données Access pour la Migration](http://msdn.microsoft.com/9b80a9e0-08e7-4b4d-b5ec-cc998d3f5114) rubrique pour déterminer ce qui sera et ne seront pas converti.  
  
## <a name="setting-conversion-options"></a>Définition des Options de Conversion  
Avant de convertir des objets, passez en revue les options de conversion de projet dans le **paramètres du projet** boîte de dialogue. À l’aide de cette boîte de dialogue, vous pouvez définir comment SSMA convertit les colonnes Mémo indexées, les clés primaires, les contraintes de clé étrangère, les horodateurs et les tables sans index. Pour plus d’informations, consultez [paramètres du projet (Conversion)](http://msdn.microsoft.com/bcebc635-c638-4ddb-924c-b9ccfef86388)  
  
## <a name="conversion-results"></a>Résultats de la conversion  
Le tableau suivant présente les objets d’accès sont convertis et résultant [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou objets de SQL Azure :  
  
|Objet d’accès|Objet qui en résulte de SQL Server|  
|-----------------|-------------------------------|  
|table|table|  
|column|column|  
|index|index|  
|clé étrangère|clé étrangère|  
|Requête|vue<br /><br />Requêtes SELECT plus sont converties en vues. Autres requêtes, telles que les requêtes de mise à jour, ne sont pas migrés.<br /><br />Les requêtes SELECT qui prennent des paramètres ne sont pas converties, ni les requêtes de tableau croisé.|  
|rapport|non converti|  
|Formulaire|non converti|  
|(Macro)|non converti|  
|module|non converti|  
|Valeur par défaut|Valeur par défaut|  
|Autoriser zéro propriété de colonne de longueur|contrainte de validation|  
|règle de validation de colonne|contrainte de validation|  
|règle de validation de table|contrainte de validation|  
|clé primaire|clé primaire|  
  
## <a name="converting-access-objects"></a>Convertir des objets d’accès  
Pour convertir des objets de base de données Access, vous devez tout d’abord sélectionner les objets que vous souhaitez convertir et puis SSMA effectuer la conversion. Pour afficher les messages de sortie pendant la conversion, sur le **vue** menu, sélectionnez **sortie**.  
  
**Pour sélectionner et convertir des objets de base de données Access à la syntaxe SQL Server ou SQL Azure**  
  
1.  Dans l’Explorateur de métadonnées d’accès, développez **la métabase accès**, puis développez **bases de données**.  
  
2.  Effectuez une ou plusieurs des opérations suivantes :  
  
    -   Pour convertir toutes les bases de données, sélectionnez la case à cocher à côté **bases de données**.  
  
    -   Pour convertir ou omettre les bases de données individuelles, sélectionnez ou désactivez la case à cocher en regard du nom de la base de données.  
  
    -   Pour convertir ou omettre des requêtes, développez la base de données, puis cochez ou décochez la **requêtes** case à cocher.  
  
    -   Pour convertir ou omettre des tables individuelles, développez la base de données, puis **Tables**, puis sélectionnez ou désactivez la case à cocher en regard du tableau.  
  
3.  Procédez de l'une des manières suivantes :  
  
    -   Pour convertir des schémas, avec le bouton droit **bases de données** et sélectionnez **convertir le schéma**.  
  
        Vous pouvez également convertir des objets individuels. Pour convertir un objet, quelles que soient les objets sont sélectionnés, cliquez sur l’objet et sélectionnez **convertir le schéma**.  
  
        Lorsqu’un objet a été converti, il apparaît en gras dans l’Explorateur de métadonnées d’accès.  
  
    -   Pour convertir, charger et migrer les schémas et les données en une seule étape, cliquez sur les bases de données et sélectionnez **convertir, charger et migrer**.  
  
4.  Passez en revue les messages dans la **sortie** volet et les erreurs et les avertissements dans le **liste d’erreurs** volet.  
  
## <a name="altering-tables-and-indexes"></a>Modification des Tables et des index  
Après avoir converti les métadonnées de l’accès à [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou les métadonnées de SQL Azure, et avant de charger les objets vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou SQL Azure, vous pouvez modifier [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou des tables de SQL Azure et des index.  
  
**Pour modifier les propriétés de table ou un index**  
  
1.  Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou l’Explorateur de métadonnées SQL Azure, sélectionnez la table ou l’index que vous souhaitez modifier.  
  
2.  Sur le **Table** , cliquez sur la propriété que vous souhaitez modifier puis entrez ou sélectionnez le nouveau paramètre. Par exemple, vous pouvez modifier nvarchar (15) à nvarchar (20), ou sélectionnez une case à cocher pour rendre une colonne de table autorise la valeur null.  
  
    Déplacez le curseur hors de la cellule de la propriété modifiée. Vous pouvez le faire en cliquant sur une autre ligne ou en appuyant sur la touche Tab.  
  
3.  Cliquez sur **Appliquer**.  
  
Vous pouvez maintenant afficher les modifications dans le code sur le **SQL** onglet.  
  
## <a name="next-step"></a>Étape suivante  
L’étape suivante du processus de migration est [charger des objets de base de données convertis dans SQL Server](http://msdn.microsoft.com/4e854eee-b10c-4f0b-9d9e-d92416e6f2ba)  
  
## <a name="see-also"></a>Voir aussi  
[Migration bases de données Access vers SQL Server](http://msdn.microsoft.com/76a3abcf-2998-4712-9490-fe8d872c89ca)  
  
