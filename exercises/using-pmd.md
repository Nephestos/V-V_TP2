# Using PMD

Pick a Java project from Github (see the [instructions](../sujet.md) for suggestions). Run PMD on its source code using any ruleset. Describe below an issue found by PMD that you think should be solved (true positive) and include below the changes you would add to the source code. Describe below an issue found by PMD that is not worth solving (false positive). Explain why you would not solve this issue.

## Answer

true positive :
CloseResource:	Ensure that resources like this PrintStream object are closed after use

final PrintStream oldSystemOut = System.out;
        try {
            final ByteArrayOutputStream bytes = new ByteArrayOutputStream();
            final PrintStream print = new PrintStream(bytes);

            // capture this platform's eol symbol
            print.println();
            final String eol = bytes.toString();
            bytes.reset();

            System.setOut(new PrintStream(bytes));

            final HelpFormatter formatter = new HelpFormatter();
            formatter.printHelp("dir", options);

            assertEquals("usage: dir" + eol + " -d <arg>   dir" + eol, bytes.toString());
        } finally {
            System.setOut(oldSystemOut);
        }

on ne ferme pas le printStream alors qu'on aurait dû

false positive:
UncommentedEmptyMethodBody


    @Override
    @Test
    @Ignore("not supported by the PosixParser")
    public void testAmbiguousLongWithoutEqualSingleDash() throws Exception {
    }

La fonction n'est pas commentée, mais ce la n'est pas grave car elle n'est pas supportée par le PosixParser
