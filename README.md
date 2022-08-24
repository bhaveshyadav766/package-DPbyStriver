package DPbyStriver;

import java.util.*;

class Planetary{
	String planet;
	List<String> gasses = new ArrayList<String>();
	int moons;
	boolean rings;
	Planetary(String planet, List<String> gasses,int moons,boolean rings){
		this.planet=planet;
		this.gasses=gasses;
		this.moons=moons;
		this.rings=rings;
	}
}
public class Planets {
	public static int countOfMoons(List<Planetary> list) {
		int count = 0;
		for(Planetary p : list)
		{
			if(p.rings)
				count+=p.moons;
		}
		return count;
	}
	public static String gasInMaximumPlanets(List<Planetary> list) {
		Map<String,Integer> map = new TreeMap<>();
		for(Planetary p : list)
		{
			List<String> s = p.gasses;
			for(String x : s)
			{
				if(map.containsKey(x))
					map.put(x, map.get(x)+1);
				else
					map.put(x, 1);
			}
		}
		String res = "";
		int max = 0;
		for(Map.Entry<String, Integer> entry : map.entrySet())
		{
			if(entry.getValue()>max)
			{
				max = entry.getValue();
				res = entry.getKey();
			}
		}
		return res;
	}
	public static void main(String[] args) {
		Planetary p1 = new Planetary("Mercury",Arrays.asList(""),0,false);
		Planetary p2 = new Planetary("Venus",Arrays.asList("Carbon Dioxide","Nitrogen"),0,false);
		Planetary p3 = new Planetary("Earth",Arrays.asList("Nitrogen","Oxygen"),1,false);
		Planetary p4 = new Planetary("Jupitor",Arrays.asList("Hydrogen","Helium"),79,true);
		Planetary p5 = new Planetary("Saturn",Arrays.asList("Hydrogen","Helium"),83,true);
		Planetary p6 = new Planetary("Uranus",Arrays.asList("Hydrogen","Helium","Methane"),27,true);
		List<Planetary> list = Arrays.asList(p1,p2,p3,p4,p5,p6);
		System.out.println("Total no. of moons = "+countOfMoons(list));
		System.out.println("Gas which is present in maximum planets : "+gasInMaximumPlanets(list));
	}
}
