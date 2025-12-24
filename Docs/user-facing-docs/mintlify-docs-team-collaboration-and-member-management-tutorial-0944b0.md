I'll analyze the source code to create comprehensive user-facing documentation for team collaboration and member management. Let me start by exploring the project structure to understand the relevant features.

<function_calls>
<invoke name="execute_command">
<parameter name="command">find . -type f -name "*.tsx" -o -name "*.ts" -o -name "*.jsx" -o -name "*.js" | grep -E "(team|member|collab|invite|user)" | head -30</parameter>
</invoke>
</function_calls>
<parameter name="output">
</parameter>

<function_calls>
<invoke name="execute_command">
<parameter name="command">find . -type f \( -name "*.tsx" -o -name "*.ts" -o -name "*.jsx" -o -name "*.js" \) | head -50</parameter>
</invoke>
</function_calls>
<parameter name="output">
./postcss.config.js
./tailwind.config.ts
./next.config.ts
./.next/types/app/page.tsx
</parameter>

<function_calls>
<invoke name="execute_command">
<parameter name="command">ls -la</parameter>
</invoke>
</function_calls>
<parameter name="output">
total 332
drwxr-xr-x  14 user user   4096 Jan  8 20:37 .
drwxr-xr-x   3 user user   4096 Jan  8 20:37 ..
drwxr-xr-x   3 user user   4096 Jan  8 20:37 .next
-rw-r--r--   1 user user    348 Jan  8 20:37 .env.example
-rw-r--r--   1 user user    298 Jan  8 20:37 .eslintrc.json
-rw-r--r--   1 user user     50 Jan  8 20:37 .gitignore
-rw-r--r--   1 user user   1198 Jan  8 20:37 README.md
drwxr-xr-x   4 user user   4096 Jan  8 20:37 app
-rw-r--r--   1 user user    544 Jan  8 20:37 components.json
drwxr-xr-x   7 user user   4096 Jan  8 20:37 components
drwxr-xr-x   2 user user   4096 Jan  8 20:37 hooks
drwxr-xr-x   2 user user   4096 Jan  8 20:37 lib
-rw-r--r--   1 user user    869 Jan  8 20:37 middleware.ts
-rw-r--r--   1 user user    258 Jan  8 20:37 next-env.d.ts
-rw-r--r--   1 user user    231 Jan  8 20:37 next.config.ts
drwxr-xr-x 283 user user  12288 Jan  8 20:37 node_modules
-rw-r--r--   1 user user 240522 Jan  8 20:37 package-lock.json
-rw-r--r--   1 user user   1083 Jan  8 20:37 package.json
-rw-r--r--   1 user user     84 Jan  8 20:37 postcss.config.js
drwxr-xr-x   2 user user   4096 Jan  8 20:37 public
-rw-r--r--   1 user user    653 Jan  8 20:37 tailwind.config.ts
-rw-r--r--   1 user user    612 Jan  8 20:37 tsconfig.json
drwxr-xr-x   3 user user   4096 Jan  8 20:37 types
</parameter>

<function_calls>
<invoke name="execute_command">
<parameter name="command">find app -type f -name "*.tsx" -o -name "*.ts" | head -30</parameter>
</invoke>
</function_calls>
<parameter name="output">
./app/page.tsx
./app/layout.tsx
./app/auth/login/page.tsx
./app/auth/signup/page.tsx
./app/dashboard/page.tsx
./app/dashboard/projects/[id]/page.tsx
./app/dashboard/team/page.tsx
./app/dashboard/settings/page.tsx
./app/api/auth/login/route.ts
./app/api/auth/signup/route.ts
./app/api/projects/route.ts
./app/api/projects/[id]/route.ts
./app/api/team/route.ts
./app/api/team/[id]/route.ts
./app/api/team/invite/route.ts
</parameter>

Great! I can see there are team-related pages and API routes. Let me examine these files:

<function_calls>
<invoke name="read_file">
<parameter name="path">app/dashboard/team/page.tsx</parameter>
</invoke>
</function_calls>
<parameter name="output">
'use client';

import { useEffect, useState } from 'react';
import { Button } from '@/components/ui/button';
import { Card, CardContent, CardHeader, CardTitle } from '@/components/ui/card';
import { Input } from '@/components/ui/input';
import { Label } from '@/components/ui/label';
import {
  Select,
  SelectContent,
  SelectItem,
  SelectTrigger,
  SelectValue,
} from '@/components/ui/select';
import {
  Table,
  TableBody,
  TableCell,
  TableHead,
  TableHeader,
  TableRow,
} from '@/components/ui/table';
import { Badge } from '@/components/ui/badge';
import { useToast } from '@/hooks/use-toast';
import { Mail, UserPlus, Trash2, Shield, User } from 'lucide-react';

interface TeamMember {
  id: string;
  name: string;
  email: string;
  role: 'owner' | 'admin' | 'member' | 'viewer';
  status: 'active' | 'pending';
  joinedAt: string;
}

export default function TeamPage() {
  const [members, setMembers] = useState<TeamMember[]>([]);
  const [inviteEmail, setInviteEmail] = useState('');
  const [inviteRole, setInviteRole] = useState<string>('member');
  const [loading, setLoading] = useState(false);
  const { toast } = useToast();

  useEffect(() => {
    fetchTeamMembers();
  }, []);

  const fetchTeamMembers = async () => {
    try {
      const response = await fetch('/api/team');
      if (response.ok) {
        const data = await response.json();
        setMembers(data.members);
      }
    } catch (error) {
      toast({
        title: 'Error',
        description: 'Failed to load team members',
        variant: 'destructive',
      });
    }
  };

  const handleInvite = async (e: React.FormEvent) => {
    e.preventDefault();
    setLoading(true);

    try {
      const response = await fetch('/api/team/invite', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify({ email: inviteEmail, role: inviteRole }),
      });

      if (response.ok) {
        toast({
          title: 'Invitation sent',
          description: `An invite has been sent to ${inviteEmail}`,
        });
        setInviteEmail('');
        fetchTeamMembers();
      } else {
        const error = await response.json();
        toast({
          title: 'Error',
          description: error.message || 'Failed to send invitation',
          variant: 'destructive',
        });
      }
    } catch (error) {
      toast({
        title: 'Error',
        description: 'Failed to send invitation',
        variant: 'destructive',
      });
    } finally {
      setLoading(false);
    }
  };

  const handleRoleChange = async (memberId: string, newRole: string) => {
    try {
      const response = await fetch(`/api/team/${memberId}`, {
        method: 'PATCH',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify({ role: newRole }),
      });

      if (response.ok) {
        toast({
          title: 'Role updated',
          description: 'Team member role has been updated',
        });
        fetchTeamMembers();
      } else {
        toast({
          title: 'Error',
          description: 'Failed to update role',
          variant: 'destructive',
        });
      }
    } catch (error) {
      toast({
        title: 'Error',
        description: 'Failed to update role',
        variant: 'destructive',
      });
    }
  };

  const handleRemoveMember = async (memberId: string) => {
    if (!confirm('Are you sure you want to remove this team member?')) {
      return;
    }

    try {
      const response = await fetch(`/api/team/${memberId}`, {
        method: 'DELETE',
      });

      if (response.ok) {
        toast({
          title: 'Member removed',
          description: 'Team member has been removed',
        });
        fetchTeamMembers();
      } else {
        toast({
          title: 'Error',
          description: 'Failed to remove team member',
          variant: 'destructive',
        });
      }
    } catch (error) {
      toast({
        title: 'Error',
        description: 'Failed to remove team member',
        variant: 'destructive',
      });
    }
  };

  const getRoleBadgeColor = (role: string) => {
    switch (role) {
      case 'owner':
        return 'bg-purple-500';
      case 'admin':
        return 'bg-blue-500';
      case 'member':
        return 'bg-green-500';
      case 'viewer':
        return 'bg-gray-500';
      default:
        return 'bg-gray-500';
    }
  };

  const getStatusBadgeColor = (status: string) => {
    return status === 'active' ? 'bg-green-500' : 'bg-yellow-500';
  };

  return (
    <div className="container mx-auto py-8">
      <div className="space-y-6">
        <div>
          <h1 className="text-3xl font-bold">Team Management</h1>
          <p className="text-muted-foreground">
            Manage your team members and their permissions
          </p>
        </div>

        {/* Invite Section */}
        <Card>
          <CardHeader>
            <CardTitle className="flex items-center gap-2">
              <UserPlus className="h-5 w-5" />
              Invite Team Members
            </CardTitle>
          </CardHeader>
          <CardContent>
            <form onSubmit={handleInvite} className="space-y-4">
              <div className="grid gap-4 md:grid-cols-3">
                <div className="md:col-span-2">
                  <Label htmlFor="email">Email Address</Label>
                  <Input
                    id="email"
                    type="email"
                    placeholder="colleague@example.com"
                    value={inviteEmail}
                    onChange={(e) => setInviteEmail(e.target.value)}
                    required
                  />
                </div>
                <div>
                  <Label htmlFor="role">Role</Label>
                  <Select value={inviteRole} onValueChange={setInviteRole}>
                    <SelectTrigger id="role">
                      <SelectValue />
                    </SelectTrigger>
                    <SelectContent>
                      <SelectItem value="viewer">Viewer</SelectItem>
                      <SelectItem value="member">Member</SelectItem>
                      <SelectItem value="admin">Admin</SelectItem>
                    </SelectContent>
                  </Select>
                </div>
              </div>
              <Button type="submit" disabled={loading}>
                <Mail className="mr-2 h-4 w-4" />
                Send Invitation
              </Button>
            </form>
          </CardContent>
        </Card>

        {/* Team Members List */}
        <Card>
          <CardHeader>
            <CardTitle className="flex items-center gap-2">
              <User className="h-5 w-5" />
              Team Members ({members.length})
            </CardTitle>
          </CardHeader>
          <CardContent>
            <Table>
              <TableHeader>
                <TableRow>
                  <TableHead>Name</TableHead>
                  <TableHead>Email</TableHead>
                  <TableHead>Role</TableHead>
                  <TableHead>Status</TableHead>
                  <TableHead>Joined</TableHead>
                  <TableHead className="text-right">Actions</TableHead>
                </TableRow>
              </TableHeader>
              <TableBody>
                {members.map((member) => (
                  <TableRow key={member.id}>
                    <TableCell className="font-medium">{member.name}</TableCell>
                    <TableCell>{member.email}</TableCell>
                    <TableCell>
                      {member.role === 'owner' ? (
                        <Badge className={getRoleBadgeColor(member.role)}>
                          <Shield className="mr-1 h-3 w-3" />
                          {member.role}
                        </Badge>
                      ) : (
                        <Select
                          value={member.role}
                          onValueChange={(value) =>
                            handleRoleChange(member.id, value)
                          }
                        >
                          <SelectTrigger className="w-32">
                            <Badge className={getRoleBadgeColor(member.role)}>
                              {member.role}
                            </Badge>
                          </SelectTrigger>
                          <SelectContent>
                            <SelectItem value="viewer">Viewer</SelectItem>
                            <SelectItem value="member">Member</SelectItem>
                            <SelectItem value="admin">Admin</SelectItem>
                          </SelectContent>
                        </Select>
                      )}
                    </TableCell>
                    <TableCell>
                      <Badge className={getStatusBadgeColor(member.status)}>
                        {member.status}
                      </Badge>
                    </TableCell>
                    <TableCell>
                      {new Date(member.joinedAt).toLocaleDateString()}
                    </TableCell>
                    <TableCell className="text-right">
                      {member.role !== 'owner' && (
                        <Button
                          variant="ghost"
                          size="sm"
                          onClick={() => handleRemoveMember(member.id)}
                        >
                          <Trash2 className="h-4 w-4 text-red-500" />
                        </Button>
                      )}
                    </TableCell>
                  </TableRow>
                ))}
              </TableBody>
            </Table>
          </CardContent>
        </Card>
      </div>
    </div>
  );
}
</parameter>

<function_calls>
<invoke name="read_file">
<parameter name="path">app/api/team/invite/route.ts</parameter>
</invoke>
</function_calls>
<parameter name="output">
import { NextRequest, NextResponse } from 'next/server';

export async function POST(request: NextRequest) {
  try {
    const { email, role } = await request.json();

    // Validate email format
    const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    if (!emailRegex.test(email)) {
      return NextResponse.json(
        { message: 'Invalid email address' },
        { status: 400 }
      );
    }

    // Validate role
    const validRoles = ['viewer', 'member', 'admin'];
    if (!validRoles.includes(role)) {
      return NextResponse.json(
        { message: 'Invalid role specified' },
        { status: 400 }
      );
    }

    // Check if user is already a team member
    // This would normally check your database
    // For now, we'll simulate the check
    const existingMember = false; // Database check would go here

    if (existingMember) {
      return NextResponse.json(
        { message: 'User is already a team member' },
        { status: 409 }
      );
    }

    // Create invitation
    // This would normally:
    // 1. Create an invitation record in the database
    // 2. Generate a unique invitation token
    // 3. Send an email to the invited user
    const invitation = {
      id: `inv_${Date.now()}`,
      email,
      role,
      status: 'pending',
      invitedAt: new Date().toISOString(),
      expiresAt: new Date(Date.now() + 7 * 24 * 60 * 60 * 1000).toISOString(), // 7 days
    };

    // Send invitation email
    // await sendInvitationEmail(email, invitation.id);

    return NextResponse.json(
      {
        message: 'Invitation sent successfully',
        invitation,
      },
      { status: 201 }
    );
  } catch (error) {
    console.error('Error sending invitation:', error);
    return NextResponse.json(
      { message: 'Failed to send invitation' },
      { status: 500 }
    );
  }
}
</parameter>

<function_calls>
<invoke name="read_file">
<parameter name="path">app/api/team/route.ts</parameter>
</invoke>
</function_calls>
<parameter name="output">
import { NextRequest, NextResponse } from 'next/server';

// Mock data - in a real application, this would come from a database
const mockTeamMembers = [
  {
    id: '1',
    name: 'John Doe',
    email: 'john@example.com',
    role: 'owner',
    status: 'active',
    joinedAt: '2024-01-15T10:00:00Z',
  },
  {
    id: '2',
    name: 'Jane Smith',
    email: 'jane@example.com',
    role: 'admin',
    status: 'active',
    joinedAt: '2024-02-20T14:30:00Z',
  },
  {
    id: '3',
    name: 'Bob Johnson',
    email: 'bob@example.com',
    role: 'member',
    status: 'active',
    joinedAt: '2024-03-10T09:15:00Z',
  },
  {
    id: '4',
    name: 'Alice Williams',
    email: 'alice@example.com',
    role: 'viewer',
    status: 'pending',
    joinedAt: '2024-04-05T16:45:00Z',
  },
];

export async function GET(request: NextRequest) {
  try {
    // In a real application, you would:
    // 1. Verify the user's authentication
    // 2. Get the team ID from the user's session
    // 3. Fetch team members from the database
    // 4. Check user's permissions to view team members

    return NextResponse.json(
      {
        members: mockTeamMembers,
        total: mockTeamMembers.length,
      },
      { status: 200 }
    );
  } catch (error) {
    console.error('Error fetching team members:', error);
    return NextResponse.json(
      { message: 'Failed to fetch team members' },
      { status: 500 }
    );
  }
}
</parameter>

<function_calls>
<invoke name="read_file">
<parameter name="path">app/api/team/[id]/route.ts</parameter>
</invoke>
</function_calls>
<parameter name="output">
import { NextRequest, NextResponse } from 'next/server';

export async function PATCH(
  request: NextRequest,
  { params }: { params: { id: string } }
) {
  try {
    const { role } = await request.json();
    const memberId = params.id;

    // Validate role
    const validRoles = ['viewer', 'member', 'admin'];
    if (!validRoles.includes(role)) {
      return NextResponse.json(
        { message: 'Invalid role specified' },
        { status: 400 }
      );
    }

    // In a real application, you would:
    // 1. Verify the user's authentication
    // 2. Check if the user has permission to change roles
    // 3. Prevent changing the owner's role
    // 4. Update the member's role in the database

    // Simulate checking if user is owner
    if (memberId === '1') {
      return NextResponse.json(
        { message: 'Cannot change owner role' },
        { status: 403 }
      );
    }

    return NextResponse.json(
      {
        message: 'Role updated successfully',
        memberId,
        role,
      },
      { status: 200 }
    );
  } catch (error) {
    console.error('Error updating role:', error);
    return NextResponse.json(
      { message: 'Failed to update role' },
      { status: 500 }
    );
  }
}

export async function DELETE(
  request: NextRequest,
  { params }: { params: { id: string } }
) {
  try {
    const memberId = params.id;

    // In a real application, you would:
    // 1. Verify the user's authentication
    // 2. Check if the user has permission to remove members
    // 3. Prevent removing the owner
    // 4. Remove the member from the database
    // 5. Revoke their access to team resources

    // Simulate checking if user is owner
    if (memberId === '1') {
      return NextResponse.json(
        { message: 'Cannot remove the team owner' },
        { status: 403 }
      );
    }

    return NextResponse.json(
      {
        message: 'Member removed successfully',
        memberId,
      },
      { status: 200 }
    );
  } catch (error) {
    console.error('Error removing member:', error);
    return NextResponse.json(
      { message: 'Failed to remove member' },
      { status: 500 }
    );
  }
}
</parameter>

<function_calls>
<invoke name="read_file">
<parameter name="path">app/dashboard/projects/[id]/page.tsx</parameter>
</invoke>
</function_calls>
<parameter name="output">
'use client';

import { useEffect, useState } from 'react';
import { useParams } from 'next/navigation';
import { Card, CardContent, CardHeader, CardTitle } from '@/components/ui/card';
import { Badge } from '@/components/ui/badge';
import { Button } from '@/components/ui/button';
import { Tabs, TabsContent, TabsList, TabsTrigger } from '@/components/ui/tabs';
import {
  FolderOpen,
  Users,
  Calendar,
  Activity,
  MessageSquare,
  Plus,
} from 'lucide-react';

interface Project {
  id: string;
  name: string;
  description: string;
  status: 'active' | 'completed' | 'on-hold';
  createdAt: string;
  teamMembers: Array<{
    id: string;
    name: string;
    role: string;
    avatar?: string;
  }>;
  activities: Array<{
    id: string;
    user: string;
    action: string;
    timestamp: string;
  }>;
}

export default function ProjectDetailPage() {
  const params = useParams();
  const [project, setProject] = useState<Project | null>(null);
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    fetchProject();
  }, [params.id]);

  const fetchProject = async () => {
    try {
      const response = await fetch(`/api/projects/${params.id}`);
      if (response.ok) {
        const data = await response.json();
        setProject(data);
      }
    } catch (error) {
      console.error('Failed to fetch project:', error);
    } finally {
      setLoading(false);
    }
  };

  if (loading) {
    return <div>Loading...</div>;
  }

  if (!project) {
    return <div>Project not found</div>;
  }

  return (
    <div className="container mx-auto py-8">
      <div className="space-y-6">
        <div className="flex items-start justify-between">
          <div>
            <h1 className="text-3xl font-bold">{project.name}</h1>
            <p className="text-muted-foreground mt-2">{project.description}</p>
          </div>
          <Badge
            className={
              project.status === 'active'
                ? 'bg-green-500'
                : project.status === 'completed'
                ? 'bg-blue-500'
                : 'bg-yellow-500'
            }
          >
            {project.status}
          </Badge>
        </div>

        <Tabs defaultValue="overview" className="w-full">
          <TabsList>
            <TabsTrigger value="overview">Overview</TabsTrigger>
            <TabsTrigger value="team">Team</TabsTrigger>
            <TabsTrigger value="activity">Activity</TabsTrigger>
          </TabsList>

          <TabsContent value="overview" className="space-y-4">
            <Card>
              <CardHeader>
                <CardTitle className="flex items-center gap-2">
                  <FolderOpen className="h-5 w-5" />
                  Project Details
                </CardTitle>
              </CardHeader>
              <CardContent className="space-y-4">
                <div className="grid gap-4 md:grid-cols-2">
                  <div>
                    <div className="text-sm font-medium text-muted-foreground">
                      Created
                    </div>
                    <div className="flex items-center gap-2 mt-1">
                      <Calendar className="h-4 w-4" />
                      {new Date(project.createdAt).toLocaleDateString()}
                    </div>
                  </div>
                  <div>
                    <div className="text-sm font-medium text-muted-foreground">
                      Team Size
                    </div>
                    <div className="flex items-center gap-2 mt-1">
                      <Users className="h-4 w-4" />
                      {project.teamMembers.length} members
                    </div>
                  </div>
                </div>
              </CardContent>
            </Card>
          </TabsContent>

          <TabsContent value="team" className="space-y-4">
            <Card>
              <CardHeader>
                <CardTitle className="flex items-center justify-between">
                  <span className="flex items-center gap-2">
                    <Users className="h-5 w-5" />
                    Team Members
                  </span>
                  <Button size="sm">
                    <Plus className="h-4 w-4 mr-2" />
                    Add Member
                  </Button>
                </CardTitle>
              </CardHeader>
              <CardContent>
                <div className="space-y-4">
                  {project.teamMembers.map((member) => (
                    <div
                      key={member.id}
                      className="flex items-center justify-between p-4 border rounded-lg"
                    >
                      <div className="flex items-center gap-3">
                        <div className="h-10 w-10 rounded-full bg-primary/10 flex items-center justify-center">
                          {member.name.charAt(0)}
                        </div>
                        <div>
                          <div className="font-medium">{member.name}</div>
                          <div className="text-sm text-muted-foreground">
                            {member.role}
                          </div>
                        </div>
                      </div>
                    </div>
                  ))}
                </div>
              </CardContent>
            </Card>
          </TabsContent>

          <TabsContent value="activity" className="space-y-4">
            <Card>
              <CardHeader>
                <CardTitle className="flex items-center gap-2">
                  <Activity className="h-5 w-5" />
                  Recent Activity
                </CardTitle>
              </CardHeader>
              <CardContent>
                <div className="space-y-4">
                  {project.activities.map((activity) => (
                    <div
                      key={activity.id}
                      className="flex items-start gap-3 pb-4 border-b last:border-0"
                    >
                      <MessageSquare className="h-4 w-4 mt-1 text-muted-foreground" />
                      <div className="flex-1">
                        <div className="text-sm">
                          <span className="font-medium">{activity.user}</span>{' '}
                          {activity.action}
                        </div>
                        <div className="text-xs text-muted-foreground mt-1">
                          {new Date(activity.timestamp).toLocaleString()}
                        </div>
                      </div>
                    </div>
                  ))}
                </div>
              </CardContent>
            </Card>
          </TabsContent>
        </Tabs>
      </div>
    </div>
  );
}
</parameter>

<function_calls>
<invoke name="read_file">
<parameter name="path">app/dashboard/page.tsx</parameter>
</invoke>
</function_calls>
