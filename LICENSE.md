public class AccountPhoneNumberUpdate {
    public static List<Account> SinglePhoneUpdate(String name, String phone_num) {
    List<Account> accList = [SELECT Id, Name, Phone FROM Account WHERE Name = :name];

    if (!accList.isEmpty()) {
        for (Account acc : accList) {
            acc.Phone = phone_num;
        }
        update accList;
    }
    return accList;
}
    
    public static List<Account> multiplePhoneUpdate(String phoneNumber) {
        List<Account> accList = [SELECT Id, Name, Phone FROM Account LIMIT 5];
       
        for (Account acc : accList) {
            acc.Phone = phoneNumber;
        }

        update accList;
        return accList;
    }
    
    public static List<Account> insertAccRecord(String name){
        List<Account> accList = New list<Account>();
        for(Integer i=1; i<=50; i++){
            Account acc = New Account();
            acc.Name = name + i;
            acc.Phone = '000111' + i;
            accList.add(acc);
            }
        insert accList;
        return accList;
    }
    
    public static List<Account> deleteAccRecordCreatedToday(){
        List<Account> accList = New List<Account>();
        accList = [SELECT Id, Name, Type, Phone FROM Account WHERE CreatedDate = TODAY];
        delete accList;
        return accList;
    }
}
