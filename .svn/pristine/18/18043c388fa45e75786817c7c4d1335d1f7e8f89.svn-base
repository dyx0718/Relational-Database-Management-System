
package db61b;
import org.junit.Test;
import static org.junit.Assert.*;
import static org.junit.matchers.JUnitMatchers.*;
import java.util.List;
import java.util.Arrays;



public class BasicTests {
    @Test
    public void testRow() {
        Row r = new Row(new String[]{"Abby", "is", "writing", "this", "test"});
        assertEquals(5, r.size());
        assertEquals("Abby", r.get(0));
        try {
            r.get(6);
            fail();
        } catch (db61b.DBException e) {
            assertThat(e.getMessage(),
                containsString("wrong column number"));
        }
        Row obj1 = new Row(new String[]
        {"Abby", "is", "writing", "this", "test"});
        Row obj2 = new Row(new String[]
        {"Yixin", "is", "writing", "this", "test"});
        Object obj3 = new String[] {"Yixin", "is", "writing", "this", "test"};
        assertTrue(r.equals(obj1));
        assertFalse(r.equals(obj2));
        try {
            r.equals(obj3);
            fail();
        } catch (db61b.DBException e) {
            assertThat(e.getMessage(),
                containsString("wrong obj input"));
        }
    }
    @Test
    public void testTable() {
        Table desk = new Table(new String[] {"SID", "Lastname"});
        Row first = new Row(new String[] {"111", "Smith"});
        Row second = new Row(new String[] {"112", "Du"});
        assertEquals(2, desk.columns());
        assertEquals(0, desk.size());
        desk.add(first);
        desk.add(second);
        assertEquals(2, desk.columns());
        assertEquals(2, desk.size());
        Table testreadwritetable = new Table(new String[]
        {"SID", "Lastname", "Firstname"});
        Row third = new Row(new String[] {"111", "Smith", "Will"});
        Row forth = new Row(new String[] {"112", "Du", "Abby"});
        testreadwritetable.add(third);
        testreadwritetable.add(forth);
        testreadwritetable.writeTable("blank");
        Table reader = testreadwritetable.readTable("blank");
        desk.print();
        Database i = new Database();
        i.put("db1", desk);
        i.put("db2", testreadwritetable);
        assertEquals(desk, i.get("db1"));
        assertEquals(testreadwritetable, i.get("db2"));
        List<String> listA = Arrays.asList("SID");
        desk.select(listA, null).print();

    }


    public static void main(String[] args) {
        System.exit(ucb.junit.textui.runClasses(BasicTests.class));
    }
}
