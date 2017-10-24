---
title: "CRÉER la clé de principale de colonne (Transact-SQL) | Documents Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SQL13.SWB.NEWCOLUMNMASTERKEYDEF.GENERAL.F1
- SQL13.SWB.COLUMNMASTERKEYDEF.GENERAL.F1
- CREATE COLUMN MASTER KEY
- COLUMN MASTER KEY
- CREATE_COLUMN_MASTER_KEY_TSQL
- COLUMN_MASTER_KEY_TSQL
- SQL13.SWB.NEWCOLUMNMASTERKEY.GENERAL.F1
- SQL13.SWB.COLUMNMASTERKEY.GENERAL.F1
dev_langs:
- TSQL
helpviewer_keywords:
- column master key definition
- column master key, create
- CREATE COLUMN MASTER KEY statement
- Always Encrypted, create column master key
ms.assetid: f8926b95-e146-4e3f-b56b-add0c0d0a30e
caps.latest.revision: 32
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 871acb46898a9a62b25062f69d4e51bf28658f06
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="create-column-master-key-transact-sql"></a>CREATE COLUMN MASTER KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Crée un objet de métadonnées de clé principale de colonne dans une base de données. Une entrée de métadonnées de clé principale de colonne qui représente une clé stockée dans un magasin de clés externe, ce qui permet de protéger (chiffrez) les clés de chiffrement de colonne lorsque vous utilisez la [Always Encrypted &#40; moteur de base de données &#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md) fonctionnalité. Permettre à plusieurs clés principales de colonne pour la rotation des clés ; modifier régulièrement la clé pour améliorer la sécurité. Vous pouvez créer une clé principale de colonne dans un magasin de clés et de l’objet de métadonnées correspondant dans la base de données à l’aide de l’Explorateur d’objets dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou PowerShell. Pour plus d’informations, consultez [vue d’ensemble de la gestion des clés pour Always Encrypted](../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
CREATE COLUMN MASTER KEY key_name   
    WITH (  
        KEY_STORE_PROVIDER_NAME = 'key_store_provider_name',  
        KEY_PATH = 'key_path'   
         )   
[;]  
```  
  
## <a name="arguments"></a>Arguments  
 *key_name*  
 Est le nom par lequel la clé principale de colonne sera connue dans la base de données.  
  
 *key_store_provider_name*  
 Spécifie le nom d’un fournisseur de magasin de clés, qui est un composant logiciel côté client qui encapsule un magasin de clés contenant la clé principale de colonne. Un pilote client compatible avec Always Encrypted utilise un nom de fournisseur de magasin de clés pour rechercher un fournisseur de magasin de clés de Registre du pilote de fournisseurs de magasin de clés. Le pilote utilise le fournisseur pour déchiffrer les clés de chiffrement de colonne, protégées par une clé principale de colonne stockée dans le magasin de clés sous-jacent. Une valeur en texte brut de la clé de chiffrement de colonne est ensuite utilisée pour chiffrer les paramètres de requête, correspondant aux colonnes de la base de données chiffrée, ou pour déchiffrer les résultats de la requête à partir des colonnes chiffrées.  
  
 Bibliothèques de pilotes toujours chiffré client prenant en charge incluent des fournisseurs de magasin de clés pour les magasins de clés populaires.   
  
Un ensemble de fournisseurs disponibles varient selon le type et la version du pilote du client. Reportez-vous à la documentation Always Encrypted pour les pilotes particuliers :

[Développer des Applications utilisant Always Encrypted avec le fournisseur .NET Framework pour SQL Server](../../relational-databases/security/encryption/develop-using-always-encrypted-with-net-framework-data-provider.md)


Les tableaux ci-après capture les noms de fournisseurs de système :  
  
|Nom de fournisseur de magasin de clés|Magasin de clés sous-jacent|  
    |-----------------------------|--------------------------|
    |'MSSQL_CERTIFICATE_STORE'|Magasin de certificats Windows| 
    |« MSSQL_CSP_PROVIDER »|Un magasin, tel qu’un module de sécurité matériel (HSM), qui prend en charge Microsoft CryptoAPI.|
    |'MSSQL_CNG_STORE'|Un magasin, tel que d’un module de sécurité matériel (HSM), qui prend en charge les API de chiffrement : nouvelle génération.|  
    |'Azure_Key_Vault'|Consultez [prise en main d’Azure Key Vault](https://azure.microsoft.com/documentation/articles/key-vault-get-started/)|  
  

 Vous pouvez implémenter un fournisseur de magasins de clés personnalisés, pour stocker les clés principales de colonne dans un magasin pour lequel il n’existe aucune clé intégré fournisseur de magasin dans le pilote client compatible avec Always Encrypted.  Notez que les noms de fournisseurs de magasins de clés personnalisé ne peut pas commencer par 'MSSQL_', qui est un préfixe réservé pour [!INCLUDE[msCoName](../../includes/msconame-md.md)] fournisseurs de magasin de clés. 

  
 key_path  
 Le chemin d’accès de la clé dans la clé principale de colonne stocker. Le chemin de clé doit être valide dans le contexte de chaque application cliente qui est prévu pour chiffrer ou déchiffrer des données stockées dans une colonne (indirectement) protégée par la clé principale de colonne référencée et l’application cliente doit être autorisé à accéder à la clé. Le format du chemin d’accès de clé est spécifique au fournisseur de magasin de clés. La liste suivante décrit le format de chemins de clés pour les fournisseurs de magasin de clés du système Microsoft particuliers.  
  
-   **Nom du fournisseur :** MSSQL_CERTIFICATE_STORE  
  
     **Format du chemin de la clé :** *CertificateStoreName*/*CertificateStoreLocation*/*CertificateThumbprint*  
  
     Où :  
  
     *CertificateStoreLocation*  
     Emplacement de magasin de certificats, qui doit être l’utilisateur actuel ou l’ordinateur Local. Pour plus d’informations, consultez [ordinateur Local et magasins de certificats utilisateur actuel](https://msdn.microsoft.com/library/windows/hardware/ff548653.aspx).  
  
     *CertificateStore*  
     Nom du magasin de certificats, par exemple 'My'.  
  
     *CertificateThumbprint*  
     Empreinte numérique du certificat.  
  
     **Exemples :**  
  
    ```  
    N'CurrentUser/My/BBF037EC4A133ADCA89FFAEC16CA5BFA8878FB94'  
  
    N'LocalMachine/My/CA5BFA8878FB94BBF037EC4A133ADCA89FFAEC16'  
    ```  
  
-   **Nom du fournisseur :** MSSQL_CSP_PROVIDER  
  
     **Format du chemin de la clé :** *ProviderName*/*KeyIdentifier*  
  
     Où :  
  
     *ProviderName*  
     Le nom d’un fournisseur de Service de chiffrement (CSP), implémentant CAPI, pour le magasin de clés principales de colonne. Si vous utilisez un module HSM comme un magasin de clés, il doit être le nom du fournisseur de votre HSM CSP fournit. Le fournisseur doit être installé sur un ordinateur client.  
  
     *Identificateur de clé*  
     Identificateur de la clé, utilisée comme clé principale de colonne, dans le magasin de clés.  
  
     **Exemples :**  
  
    ```  
    N'My HSM CSP Provider/AlwaysEncryptedKey1'  
    ```  
  
-   **Nom du fournisseur :** MSSQL_CNG_STORE  
  
     **Format du chemin de la clé :** *ProviderName*/*KeyIdentifier*  
  
     Où :  
  
     *ProviderName*  
     Nom de la clé de stockage fournisseur (KSP), qui implémente le chiffrement : Next Generation (CNG) API, pour le magasin de clés principales de colonne. Si vous utilisez un module HSM comme un magasin de clés, il doit être le nom de votre fournisseur HSM KSP fournit. Le fournisseur doit être installé sur un ordinateur client.  
  
     *Identificateur de clé*  
     Identificateur de la clé, utilisée comme clé principale de colonne, dans le magasin de clés.  
  
     **Exemples :**  
  
    ```  
    N'My HSM CNG Provider/AlwaysEncryptedKey1'  
    ```  

-   **Nom du fournisseur :** AZURE_KEY_STORE  
  
     **Format du chemin de la clé :** *KeyUrl*  
  
     Où :  
  
     *KeyUrl*  
     L’URL de la clé dans le coffre de clés Azure


Exemple :
 
`N'https://myvault.vault.azure.net:443/keys/MyCMK/4c05f1a41b12488f9cba2ea964b6a700'`  
  
## <a name="remarks"></a>Notes  

Création d’une entrée de métadonnées de clé principale de colonne est requise avant de pouvoir créer une entrée de métadonnées de clé de chiffrement de colonne dans la base de données et avant toute colonne dans la base de données peut être chiffrée à l’aide d’Always Encrypted. Notez que, une entrée de clé principale de colonne dans les métadonnées ne contienne pas de la clé principale de colonne réelle, qui doit être stockée dans un magasin de clés de colonne externe (en dehors de SQL Server). Le nom de fournisseur de magasin de clés et le chemin d’accès de clé principale de colonne dans les métadonnées doivent être valides pour une application cliente pour être en mesure d’utiliser la clé principale de colonne pour déchiffrer une clé de chiffrement de colonne chiffrée avec la clé principale de colonne et pour interroger des colonnes chiffrées.


  
## <a name="permissions"></a>Permissions  
 Requiert le **ALTER ANY COLUMN MASTER KEY** autorisation.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-creating-a-column-master-key"></a>A. Création d’une clé principale de colonne  
 Création d’une entrée de métadonnées de clé principale de colonne pour une clé principale de colonne stockée dans le magasin de certificats pour les applications clientes qui utilisent le fournisseur MSSQL_CERTIFICATE_STORE pour accéder à la clé principale de colonne :  
  
```  
CREATE COLUMN MASTER KEY MyCMK  
WITH (  
     KEY_STORE_PROVIDER_NAME = N'MSSQL_CERTIFICATE_STORE',   
     KEY_PATH = 'Current User/Personal/f2260f28d909d21c642a3d8e0b45a830e79a1420'  
   );  
```  
  
 Création d’une entrée de métadonnées de clé principale de colonne pour une clé principale de colonne qui est accessible par les applications clientes qui utilisent le fournisseur MSSQL_CNG_STORE :  
  
```  
CREATE COLUMN MASTER KEY MyCMK  
WITH (  
    KEY_STORE_PROVIDER_NAME = N'MSSQL_CNG_STORE',    
    KEY_PATH = N'My HSM CNG Provider/AlwaysEncryptedKey'  
);  
```  
  
 Création d’une clé principale de colonne stockée dans le coffre de clés Azure, pour les applications clientes qui utilisent le fournisseur AZURE_KEY_VAULT, pour accéder à la clé principale de colonne.  
  
```  
CREATE COLUMN MASTER KEY MyCMK  
WITH (  
    KEY_STORE_PROVIDER_NAME = N'AZURE_KEY_VAULT',  
    KEY_PATH = N'https://myvault.vault.azure.net:443/keys/  
        MyCMK/4c05f1a41b12488f9cba2ea964b6a700');  
```  
  
 Création d’une clé CMK stockée dans un magasin de clés principales de colonne personnalisée :  
  
```  
CREATE COLUMN MASTER KEY MyCMK  
WITH (  
    KEY_STORE_PROVIDER_NAME = 'CUSTOM_KEY_STORE',    
    KEY_PATH = 'https://contoso.vault/sales_db_tce_key'  
);  
```  
  
## <a name="see-also"></a>Voir aussi
 
* [SUPPRIMER la clé principale de colonne &#40; Transact-SQL &#41;](../../t-sql/statements/drop-column-master-key-transact-sql.md)   
* [CREATE COLUMN ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-column-encryption-key-transact-sql.md)
* [sys.column_master_keys (Transact-SQL)](../../relational-databases/system-catalog-views/sys-column-master-keys-transact-sql.md)
* [Always Encrypted &#40;moteur de base de données&#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md)  
* [Vue d’ensemble de la gestion des clés pour Always Encrypted](../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md)
  

