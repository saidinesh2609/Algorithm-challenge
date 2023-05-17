## Code
```
import java.util.HashSet;
import java.util.Set;

public class LifeformFinder {
    public static int calculateLifeformScore(String layout) {
        int score = 0;
        for (int i = 0; i < layout.length(); i++) {
            if (layout.charAt(i) == 'X') {
                score += Math.pow(2, i);
            }
        }
        return score;
    }

    public static String findFirstDuplicateLayout(String layout) {
        Set<String> seenLayouts = new HashSet<>();
        while (!seenLayouts.contains(layout)) {
            seenLayouts.add(layout);
            StringBuilder nextLayout = new StringBuilder();
            for (int i = 0; i < layout.length(); i++) {
                int numLifeforms = countAdjacentLifeforms(layout, i);
                if (layout.charAt(i) == 'X' && numLifeforms == 1) {
                    nextLayout.append('X');
                } else if (layout.charAt(i) == '.' && (numLifeforms == 1 || numLifeforms == 2)) {
                    nextLayout.append('X');
                } else {
                    nextLayout.append('.');
                }
            }
            layout = nextLayout.toString();
        }
        return layout;
    }

    public static int countAdjacentLifeforms(String layout, int index) {
        int numLifeforms = 0;
        int[] dx = {0, 0, 1, -1};
        int[] dy = {1, -1, 0, 0};
        int x = index % 5;
        int y = index / 5;
        for (int j = 0; j < 4; j++) {
            int nx = x + dx[j];
            int ny = y + dy[j];
            if (0 <= nx && nx < 5 && 0 <= ny && ny < 5 && layout.charAt(ny * 5 + nx) == 'X') {
                numLifeforms++;
            }
        }
        return numLifeforms;
    }

    public static void main(String[] args) {
        String[] startState = {
                "XXXX.",
                "X....",
                "X..X.",
                ".X.X.",
                "XX.XX"
        };

        String layout = String.join("", startState);

        String duplicateLayout = findFirstDuplicateLayout(layout);
        int lifeformScore = calculateLifeformScore(duplicateLayout);

        System.out.println("Duplicate layout:");
        for (int i = 0; i < duplicateLayout.length(); i += 5) {
            System.out.println(duplicateLayout.substring(i, i + 5));
        }
        System.out.println("Lifeform score: " + lifeformScore);
    }
}
```

## Output
```
java -cp /tmp/4B1MHykT2t LifeformFinder
Duplicate layout:XXXXX
.....
..X..
.....
XXXXX
Lifeform score: 32509983
```

