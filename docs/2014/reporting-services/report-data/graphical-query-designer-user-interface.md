---
title: Interface utilisateur du concepteur de requêtes graphique | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10012"
- sql12.rtp.rptdesigner.dataview.vdtquerydesigner.f1
helpviewer_keywords:
- graphical query designer [Reporting Services]
- data sources [Reporting Services], creating
- text-based query designer [Reporting Services]
- query designers [Reporting Services]
- Reporting Services, query designers
ms.assetid: 5022ae33-03a3-48de-8ac1-82742f48cebe
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 27b487c787a82f67fc861153939eb5838373fca1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48107999"
---
# <a name="graphical-query-designer-user-interface"></a>Interface utilisateur du concepteur de requêtes graphique
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] fournit un concepteur de requêtes graphique et un concepteur de requêtes textuel pour la création de requêtes permettant de récupérer des données d’une base de données relationnelle pour un dataset de rapport dans le Concepteur de rapports. Utilisez le concepteur de requêtes graphique pour générer une requête de manière interactive et afficher les résultats pour les types de sources de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], Oracle, OLE DB et ODBC. Utilisez le concepteur de requêtes textuel pour spécifier plusieurs instructions [!INCLUDE[tsql](../../../includes/tsql-md.md)] , une syntaxe de requête ou de commande complexe et des requêtes basées sur des expressions. Pour plus d’informations, consultez [Interface utilisateur du Concepteur de requêtes textuel](../text-based-query-designer-user-interface.md). Pour plus d’informations sur l’utilisation des types de sources de données spécifiques, consultez [ajouter des données à un rapport &#40;Générateur de rapports et SSRS&#41;](report-datasets-ssrs.md).  
  
 .  
  
## <a name="graphical-query-designer"></a>Concepteur de requêtes graphique  
 Ce concepteur de requêtes graphique prend en charge trois types de commandes de requête : **Text**, **StoredProcedure**ou **TableDirect**. Avant de créer une requête pour votre dataset, vous devez sélectionner une option de type de commande dans la page Requête de la boîte de dialogue [Propriétés du dataset](../dataset-properties-dialog-box-query.md) .  
  
 Les options suivantes sont disponibles pour le type de requête :  
  
-   **Text** Prend en charge le texte de requête [!INCLUDE[tsql](../../../includes/tsql-md.md)] standard pour les sources de données d’une base de données relationnelle, notamment les extensions pour le traitement des données pour [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et Oracle.  
  
-   **TableDirect** Sélectionne toutes les colonnes de la table spécifiée. Par exemple, cela revient à utiliser l'instruction [!INCLUDE[tsql](../../../includes/tsql-md.md)] `SELECT * FROM Customers`pour une table nommée Customers.  
  
-   **StoredProcedure** Prend en charge les appels aux procédures stockées de la source de données. Pour utiliser cette option, les autorisations d'exécution doivent vous être accordées sur la procédure stockée par l'administrateur de la base de données sur la source de données.  
  
 Le type de commande par défaut est **Text**.  
  
> [!NOTE]  
>  Tous les types ne sont pas pris en charge par toutes les extensions de traitement de données. Le fournisseur de données sous-jacent doit prendre en charge un type de commande pour que l'option soit disponible.  
  
### <a name="command-type-text"></a>Texte de type de commande  
 Avec le type **Text** , le concepteur de requêtes graphique présente quatre zones, ou volets. Vous pouvez spécifier des colonnes, des alias, des valeurs de tri et des valeurs de filtre pour une requête [!INCLUDE[tsql](../../../includes/tsql-md.md)] . Vous pouvez afficher le texte de la requête générée à partir de vos sélections, exécuter la requête et afficher le jeu de résultats. La figure suivante représente les quatre volets.  
  
 ![Concepteur de requêtes graphique pour requêtes SQL](../media/rsqd-dsaw-sql.gif "Concepteur de requêtes graphique pour requêtes SQL")  
  
 Le tableau ci-dessous décrit la fonction de chaque volet.  
  
|Volet|Fonction|  
|----------|--------------|  
|Schéma|Affiche des représentations graphiques des tables de la requête. Ce volet permet de sélectionner des champs et de définir des relations entre les tables.|  
|Grille|Affiche une liste des champs retournés par la requête. Ce volet permet de définir des alias, un ordre de tri, des filtres, des groupes et des paramètres.|  
|SQL|Affiche la requête [!INCLUDE[tsql](../../../includes/tsql-md.md)] représentée par les volets Schéma et Grille. Ce volet permet d’écrire ou de mettre à jour une requête à l’aide de [!INCLUDE[tsql](../../../includes/tsql-md.md)].|  
|Résultats|Affiche les résultats de la requête. Pour exécuter la requête, cliquez avec le bouton droit dans un volet et cliquez sur **Exécuter**, ou cliquez sur le bouton **Exécuter** dans la barre d’outils.|  
  
 Lorsque vous modifiez des informations dans un des trois premiers volets, ces modifications sont reflétées dans les autres volets. Par exemple, si vous ajoutez une table au volet Schéma, cette table est automatiquement ajoutée à la requête [!INCLUDE[tsql](../../../includes/tsql-md.md)] dans le volet SQL. L'ajout d'un champ à la requête dans le volet SQL entraîne l'insertion du champ dans la liste du volet Grille et la mise à jour de la table dans le volet Diagramme.  
  
 Pour plus d’informations, consultez [Outils du concepteur de requêtes et de vues &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/visual-database-tools.md).  
  
#### <a name="toolbar-for-the-graphical-query-designer"></a>Barre d’outils du concepteur de requêtes graphique  
 La barre d’outils du concepteur de requêtes graphique fournit des boutons pour concevoir des requêtes [!INCLUDE[tsql](../../../includes/tsql-md.md)] à l’aide de l’interface graphique.  
  
|Bouton|Description|  
|------------|-----------------|  
|**Modifier en tant que texte**|Bascule entre le Concepteur de requêtes textuel et le concepteur de requêtes graphique.|  
|**Importer**|Importe une requête existante à partir d'un fichier ou d'un rapport. Seuls les types de fichiers .sql et .rdl sont pris en charge. Pour plus d’informations, consultez [Datasets incorporés dans les rapports et datasets partagés &#40;Générateur de rapports et SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).|  
|![Bouton bascule Afficher/Masquer le volet Diagramme](../media/rsqdicon-showhidediagram.gif "Bouton bascule Afficher/Masquer le volet Diagramme")|Affiche ou masque le volet Diagramme.|  
|![Bouton bascule Afficher/Masquer le volet Grille](../media/rsqdicon-showhidegrid.gif "Bouton bascule Afficher/Masquer le volet Grille")|Affiche ou masque le volet Grille.|  
|![Bouton bascule Afficher/Masquer le volet SQL](../media/rsqdicon-showhidesql.gif "Bouton bascule Afficher/Masquer le volet SQL")|Affiche ou masque le volet SQL.|  
|![Bouton bascule Afficher/Masquer le volet Résultats](../media/rsqdicon-showhideresult.gif "Bouton bascule Afficher/Masquer le volet Résultats")|Affiche ou masque le volet Résultat.|  
|![Exécuter la requête](../../analysis-services/media/rsqdicon-run.gif "Exécuter la requête")|Exécute la requête.|  
|![Bouton Vérifier SQL dans le volet SQL](../media/rsqdicon-verifysql.gif "Bouton Vérifier SQL dans le volet SQL")|Vérifie que la syntaxe du texte de la requête est correcte.|  
|![Définir Tri croissant sur le champ sélectionné](../media/rsqdicon-sortascending.gif "Définir Tri croissant sur le champ sélectionné")|Définit l’ordre de tri **Tri croissant** pour la colonne sélectionnée dans le volet Schéma.|  
|![Définir Tri décroissant sur le champ sélectionné](../media/rsqdicon-sortdescending.gif "Définir Tri décroissant sur le champ sélectionné")|Définit l’ordre de tri **Tri décroissant** pour la colonne sélectionnée dans le volet Schéma.|  
|![Supprimer le filtre du champ sélectionné](../media/rsqdicon-removefilter.gif "Supprimer le filtre du champ sélectionné")|Supprime le filtre pour la colonne sélectionnée dans le volet Diagramme et signalée comme comportant un filtre (![Filtre graphique à côté de la colonne filtrée sélectionnée](../media/rsqdicon-filter.gif "Filtre graphique à côté de la colonne filtrée sélectionnée")).|  
|![Utiliser Regrouper par pour le champ sélectionné](../media/rsqdicon-usegroupby.gif "Utiliser Regrouper par pour le champ sélectionné")|Affiche ou masque la colonne **Regrouper par** dans le volet Grille. Quand le bouton bascule **Regrouper par** est activé, une colonne supplémentaire intitulée **Regrouper par** s’affiche dans le volet Grille et chaque valeur pour les colonnes sélectionnées dans la requête prend par défaut la valeur **Regrouper par**, ce qui a pour effet d’inclure la colonne sélectionnée dans une clause GROUP BY dans le texte SQL. Utilisez le bouton Regrouper par pour ajouter automatiquement une clause GROUP BY qui inclut toutes les colonnes dans la clause SELECT. Si votre clause SELECT inclut des appels de fonction d'agrégation (par exemple, SUM(ColumnName)), vous devez inclure chaque colonne de non agrégation dans la clause GROUP BY si vous souhaitez qu'elle s'affiche dans le jeu de résultats.<br /><br /> Pour qu'elle s'affiche dans le volet Résultat, chaque colonne de la requête doit avoir une fonction d'agrégation définie pour être utilisée dans le calcul de la valeur à afficher dans le volet Résultat, ou alors la colonne de la requête doit être spécifiée dans la clause GROUP BY de la requête SQL.|  
|![Ajouter une table au volet Diagramme](../media/rsqdicon-addtable.gif "Ajouter une table au volet Diagramme")|Ajoute une nouvelle table à partir de la source de données dans le volet Diagramme.<br /><br /> **Remarque** Quand vous ajoutez une nouvelle table, le concepteur de requêtes tente de faire correspondre des relations de clé étrangère depuis la source de données. Après avoir ajouté la table, confirmez que les relations de clé étrangère représentées par des liaisons entre les tables sont correctes.|  
  
#### <a name="example"></a>Exemple  
 La requête suivante retourne la liste des noms depuis la table [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] Person **de la base de données** :  
  
```  
SELECT LastName FROM Person.Person;  
```  
  
 Vous pouvez également exécuter des procédures stockées à partir du volet SQL. La requête suivante exécute la procédure stockée **uspGetEmployeeManagers** dans la base de données [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] :  
  
```  
EXEC uspGetEmployeeManagers '1';  
```  
  
### <a name="command-type-tabledirect"></a>Type de commande TableDirect  
 Avec le type **TableDirect** , le concepteur de requêtes graphique affiche une liste déroulante des tables disponibles dans la source de données, ainsi qu’un volet Résultats. Si vous sélectionnez une table et cliquez sur le bouton **Exécuter** , toutes les colonnes pour cette table sont retournées.  
  
> [!NOTE]  
>  La fonctionnalité TableDirect est prise en charge uniquement par les types de sources de données **OLE DB** et **ODBC** .  
  
 Le tableau ci-dessous décrit la fonction de chaque volet.  
  
|Volet|Fonction|  
|----------|--------------|  
|Liste déroulante Table|Répertorie toutes les tables disponibles dans la source de données. Sélectionnez-en une dans la liste pour l'activer.|  
|Résultats|Affiche toutes les colonnes de la table sélectionnée. Pour exécuter la requête de table, cliquez sur le bouton **Exécuter** dans la barre d’outils.|  
  
#### <a name="toolbar-buttons-for-the-command-type-tabledirect"></a>Boutons de la barre d'outils pour le type de commande TableDirect  
 Le concepteur de requêtes graphique fournit une liste déroulante de tables dans la source de données. Le tableau suivant répertorie chaque bouton et décrit sa fonction.  
  
|Bouton|Description|  
|------------|-----------------|  
|**Modifier en tant que texte**|Bascule entre le Concepteur de requêtes textuel et le concepteur de requêtes graphique.|  
|**Importer**|Importe une requête existante à partir d'un fichier ou d'un rapport. Seuls les types de fichiers .sql et .rdl sont pris en charge. Pour plus d’informations, consultez [Datasets incorporés dans les rapports et datasets partagés &#40;Générateur de rapports et SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).|  
|![Icône du bouton du concepteur de requêtes générique](../media/icongenericquerydesigner.gif "Icône du bouton du concepteur de requêtes générique")|Bascule entre le Concepteur de requêtes générique et le concepteur de requêtes graphique, tout en conservant le texte de la requête ou la vue de la procédure stockée.|  
|![Exécuter la requête](../../analysis-services/media/rsqdicon-run.gif "Exécuter la requête")|Sélectionne toutes les colonnes de la table sélectionnée.|  
  
### <a name="command-type-storedprocedure"></a>Type de commande StoredProcedure  
 Avec le type **StoredProcedure** , le concepteur de requêtes graphique affiche une liste déroulante des procédures stockées disponibles dans la source de données, ainsi qu’un volet Résultats. Le tableau ci-dessous décrit la fonction de chaque volet.  
  
|Volet|Fonction|  
|----------|--------------|  
|Liste déroulante Procédure stockée|Répertorie toutes les procédures stockées disponibles dans la source de données. Sélectionnez-en une dans la liste pour l'activer.|  
|Résultats|Affiche les résultats de l'exécution de la procédure stockée. Pour exécuter la procédure stockée sélectionnée, cliquez sur le bouton **Exécuter** dans la barre d’outils.|  
  
#### <a name="toolbar-buttons-for-command-type-storedprocedure"></a>Boutons de la barre d'outils pour le type de commande StoredProcedure  
 La barre d'outils du concepteur de requêtes graphique fournit une liste déroulante de procédures stockées dans la source de données. Le tableau suivant répertorie chaque bouton et décrit sa fonction.  
  
|Bouton|Description|  
|------------|-----------------|  
|**Modifier en tant que texte**|Bascule entre le Concepteur de requêtes textuel et le concepteur de requêtes graphique.|  
|**Importer**|Importe une requête existante à partir d'un fichier ou d'un rapport. Seuls les types de fichiers .sql et .rdl sont pris en charge. Pour plus d’informations, consultez [Datasets incorporés dans les rapports et datasets partagés &#40;Générateur de rapports et SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).|  
|![Exécuter la requête](../../analysis-services/media/rsqdicon-run.gif "Exécuter la requête")|Exécute la procédure stockée sélectionnée.|  
|Liste déroulante Procédure stockée|Cliquez sur la flèche vers le bas pour afficher une liste des procédures stockées disponibles dans la source de données. Cliquez sur une procédure stockée de la liste pour la sélectionner.|  
  
#### <a name="example"></a>Exemple  
 La procédure stockée suivante appelle une liste de ligne hiérarchique de responsables à partir de la base de données [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] . Cette procédure stockée accepte *BusinessEntityID* en tant que paramètre. Vous pouvez spécifier un entier plus petit.  
  
 `uspGetEmployeeManagers '1';`  
  
## <a name="see-also"></a>Voir aussi  
 [Interroger des outils de conception dans le rapport concepteur SQL Server Data Tools &#40;SSRS&#41;](query-design-tools-ssrs.md)   
 [Ajouter des données à un rapport &#40;Générateur de rapports et SSRS&#41;](report-datasets-ssrs.md)   
 [Type de connexion SQL Server &#40;SSRS&#41;](sql-server-connection-type-ssrs.md)   
 [Type de connexion OLE DB &#40;SSRS&#41;](ole-db-connection-type-ssrs.md)   
 [Ajouter des données à un rapport &#40;Générateur de rapports et SSRS&#41;](report-datasets-ssrs.md)   
 [Type de connexion Oracle &#40;SSRS&#41;](oracle-connection-type-ssrs.md)   
 [Fichier de configuration RSReportDesigner](../report-server/rsreportdesigner-configuration-file.md)   
 [Rubriques de procédures relatives à la conception de requêtes et de vues &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
