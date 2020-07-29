# SimpleSQL
SimpleSQL use

        //database connection
        SqlFramework.get().setConnection("127.0.0.1","database","root","");
        
        //innerjoin table condition table condition
        ResultSet result1 =SqlFramework.get().joinTable("account",
                new String[]{"*"},
                new String[]{"client"},
                new String[]{"account.client_id=client.id"});
        
        //create new table cols names val types
        SqlFramework.get().createTable("newTable",
                new String[]{"id","someName","someNumber"},
                new ValType[]{ValType.INT,ValType.VARCHAR45,ValType.FLOAT});
        
        //insert table cols vals
        SqlFramework.get().insert("newTable",
                new String[]{"id","someName","someNumber"},
                new String[]{"1","name","96666666"});

        // update table where col=val update cols with val
        SqlFramework.get().update("client","address","Idval",
                new String[]{"address","name"},
                new String[]{"45","jim"});
        
        // update table where id update cols with val
        SqlFramework.get().update("client","12",
                new String[]{"name","address"},
                new String[]{"jose","new Street"});
        
        //delete from table where coll = val
        SqlFramework.get().delete("account","type",
                new String[]{"saving"});

        //select all from table
        ResultSet result= SqlFramework.get().select("client");
        
        //iterate through the results
        try {
            while (result.next()) {
                System.out.println(result.getString("id")+" "+result.getString("name")+" "+result.getString("adress")+" "+result.getString("phone"));
                ResultSet r= SqlFramework.get().select("client","id=10");
                if(r.next()){
                    System.out.println("not Null");
                }
            }
        }catch (Exception e){

        }
