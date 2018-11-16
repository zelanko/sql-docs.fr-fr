---
title: Paramètres (Migration) (AccessToSQL) du projet | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Migration settings
- Project Settings dialog box, Migration
ms.assetid: 4caebc9c-8680-4b99-a8fa-89c43161c95d
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 441366208d2bfd886794dd7e50dca7e0aef7b3ff
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51659338"
---
# <a name="project-settings-migration-accesstosql"></a>Paramètres du projet (Migration) (AccessToSQL)
Les paramètres de projet de Migration vous permettent de configurer la façon dont les données sont migrées à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure.  
  
Le volet de la Migration est disponible dans le **paramètres du projet** et **par défaut des paramètres de projet** boîtes de dialogue.  
  
-   Utilisez le **paramètres du projet** boîte de dialogue pour définir les options de configuration pour le projet actuel. Pour accéder aux paramètres de migration, sur le **outils** menu, sélectionnez **paramètres du projet**, cliquez sur **général** en bas du volet gauche, puis cliquez sur  **Migration**.  
  
-   Utilisez le **par défaut des paramètres de projet** boîte de dialogue pour définir les options de configuration pour tous les projets. Pour accéder aux paramètres de migration, sur le **outils** menu, sélectionnez **par défaut des paramètres de projet**, sélectionnez le type de projet dans **Version cible de Migration** zone de liste déroulante dont vous Pour accéder aux paramètres, cliquez sur **général** en bas du volet gauche, puis cliquez sur **Migration**.  
  
## <a name="options"></a>Options  
**Contraintes de validation**  
Spécifie si SSMA doit vérifier les contraintes lorsqu’il ajoute des données aux tables.  
  
-   **Par défaut en Mode**: False  
  
-   **Mode optimiste**: True  
  
-   **Mode plein**: False  
  
**Exécuter les déclencheurs**  
Spécifie si SSMA doit exécuter les déclencheurs d’insertion lorsqu’il ajoute des données à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tables.  
  
-   **Par défaut en Mode**: False  
  
-   **Mode optimiste**: True  
  
-   **Mode plein**: False  
  
**Conserver l'identité**  
Spécifie si SSMA conserve les valeurs d’identité accès lorsqu’il ajoute des données à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si cette valeur est False, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] assigne des valeurs d’identité.  
  
-   **Par défaut en Mode**: True  
  
-   **Mode optimiste**: True  
  
-   **Mode plein**: False  
  
**Conserver les valeurs NULL**  
Spécifie si SSMA conserve les valeurs null dans la source de données lorsqu’il ajoute des données à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], quels que soient les valeurs par défaut qui sont spécifiés dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   **Par défaut en Mode**: True  
  
-   **Mode optimiste**: False  
  
-   **Mode plein**: True  
  
**Verrous de table**  
Spécifie si SSMA verrouille les tables lorsqu’il ajoute des données aux tables pendant la migration de données. Si la valeur est False, SSMA utilise des verrous de ligne.  
  
-   **Par défaut en Mode**: True  
  
-   **Mode optimiste**: True  
  
-   **Mode plein**: True  
  
**Remplacer les dates non pris en charge**  
Spécifie si SSMA devrait corriger les dates d’accès qui sont antérieurs au plus tôt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] date/heure date (01 janvier 1753).  
  
-   Pour conserver les valeurs de date actuel, sélectionnez **ne rien faire**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’accepte pas les dates antérieures au 01 janvier 1753 dans une colonne datetime. Si vous utilisez des dates antérieures, vous devez convertir les valeurs datetime aux valeurs de caractère.  
  
-   Pour convertir les dates antérieures au 01 janvier 1753 avec la valeur NULL, sélectionnez **remplacer par NULL**.  
  
-   Pour remplacer les dates antérieures au 01 janvier 1753 avec une date de prise en charge, sélectionnez **remplacer par le plus proche de date pris en charge**. Si vous sélectionnez cette valeur, par défaut le plus proche date pris en charge soit sélectionné comme 01 janvier 1753.  
  
**Taille de lot**  
Taille de lot utilisée pendant la migration de données. Une transaction est enregistrée après chaque lot. Par défaut, la taille de lot pour tous les schémas est 10 000.  
  
## <a name="see-also"></a>Voir aussi  
[Reference(Access) d’Interface utilisateur](https://msdn.microsoft.com/af24c303-4a41-449b-9c86-d6558a97e839)  
  
